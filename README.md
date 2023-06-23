# Talent Suite Orchestration service

This service will be orchestrating all the business processes.

It also contains the scenario workflow data diagrams

<div hidden>
```
@startuml Adding a report

Reporter->UI: LogIn
UI->Reporter: Response
UI->ClientsAPI: Fetch project & client data
ClientsAPI->UI:
Reporter->UI: CreateReport()
UI->ReportAPI: FetchData()
ReportAPI->UI: Response Data
UI->Reporter: Form Data
Reporter->UI: SubmitForm()
UI->ReportAPI: PostData()
ReportAPI->ReportAPI: StoreReport
ReportAPI->MessagingPlatform: RaiseReportAddedEvent
ReportAPI->UI:
UI->Reporter:
MessagingPlatform->NotificationService: ReceivedReportAddedEvent()
NotificationService->NotificationService: ApplyNotificationRules
alt RAGStatusRed
  NotificationService->UserService: WhoWantsThisReport()
  UserService->NotificationService:
  NotificationService->NotificationService: GenerateEmailContent()
  NotificationService->EmailService: SendAnEmail()
  EmailService->NotificationService:
end
		
@enduml
```
</div>

![](Adding_a_report.svg)