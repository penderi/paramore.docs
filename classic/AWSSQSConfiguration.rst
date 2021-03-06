Paramore
========

Libraries and supporting examples for use with the Ports and Adapters
and CQRS architectural styles for .NET, with support for Task Queues

`View the Project on GitHub
iancooper/Paramore <https://github.com/iancooper/Paramore>`__

-  `Download **ZIP
   File** <https://github.com/iancooper/Paramore/zipball/master>`__
-  `Download **TAR
   Ball** <https://github.com/iancooper/Paramore/tarball/master>`__
-  `View On **GitHub** <https://github.com/iancooper/Paramore>`__

`Paramore Home <../index.html>`__

`Brighter Home <Brighter.html>`__

`Next <AsyncDispatchARequest.html>`__

`Prev <RunningUnderAWSSQSInfrastructure.html>`__

Brighter
========

AWS SQS Configuration
---------------------

Getting your application to interact with SQS using Brighter is a
trivial task. Simply add your AWS Credential information in *<aws/>*
section in your configuration file and ensure that an instance of
*SqsMessageProducer* is being used when building the command processor.

Here's an example of an App.config file:

::

    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
        <configSections>
            <section name="aws" type="Amazon.AWSSection, AWSSDK" />
        </configSections>
        <aws profileName="brigter.sqs.test" region="eu-west-1" />
    </configuration>
             

Brightor will not generate the SQS queues on fly. It is required to
create them before hand and define their url in service activator
configuration section.

Here's an example of service activator configuration:

::

    <serviceActivatorConnections>
        <connections>
            <add connectionName="paramore.example.documentsandfolders.documentcreatedevent" channelName="https://sqs.eu-west-1.amazonaws.com/027649620536/DocumentCreatedEvent" routingKey="DocumentCreatedEvent" dataType="DocumentsAndFolders.Sqs.Ports.Events.DocumentCreatedEvent" timeOutInMilliseconds="5000" requeueDelayInMilliseconds="5000" noOfPerformers="10" />
            <add connectionName="paramore.example.documentsandfolders.documentupdatedevent" channelName="https://sqs.eu-west-1.amazonaws.com/027649620536/DocumentUpdatedEvent" routingKey="DocumentUpdatedEvent" dataType="DocumentsAndFolders.Sqs.Ports.Events.DocumentUpdatedEvent" timeOutInMilliseconds="5000" requeueDelayInMilliseconds="5000" noOfPerformers="10" />
            <add connectionName="paramore.example.documentsandfolders.foldercreateddevent" channelName="https://sqs.eu-west-1.amazonaws.com/027649620536/FolderCreatedEvent" routingKey="FolderCreatedEvent" dataType="DocumentsAndFolders.Sqs.Ports.Events.FolderCreatedEvent" timeOutInMilliseconds="5000" requeueDelayInMilliseconds="5000" noOfPerformers="10" />
        </connections>
    </serviceActivatorConnections>
             

This project is maintained by
`iancooper <https://github.com/iancooper>`__

Hosted on GitHub Pages — Theme by
`orderedlist <https://github.com/orderedlist>`__

