---
title: "CruiseControl and Tomcat not finding log file"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by tedk on 2007-05-20
I'm running Ubuntu Dapper (we stayed with Dapper because support was until 2011) and trying to look at CruiseControl results with a Web browser and am having tons of difficulty.

The difficulty I have is that I want to look at my CruiseControl results with my Web Browser (Firefox). I'm also running apache and tomcat. The problem is that when looking at the CruiseControl webapp with tomcat, it always tries to open a defunct log file. I even brought up the JMX console and explicitly set the log dir to what I want it to be but to no effect.

I made a war file for tomcat by entering 
```
ted@halibut:/opt/cruisecontrol-2.6.2/reporting/jsp$ sh build.sh war
```

I added an override.properties file in the jsp directory
```
ted@halibut:/opt/cruisecontrol-2.6.2/reporting/jsp$ cat override.properties
user.log.dir=/opt/build.ecf/logs
user.build.status.file=ECFcurrentbuildstatus.txt
cruise.build.artifacts.dir=/opt/build.ecf/logs
```

When I put the URL [http://localhost:8080/cruisecontrol](http://localhost:8080/cruisecontrol) in Firefox, I get the following error
```
Context parameter logDir needs to be set to a directory. Currently set to "/home/ted/builds/logs "

```

At the risk of making this post too long, here is the config.xml file used by CruiseControl
```
<cruisecontrol>
  <project name="ecf" buildafterfailed="false">

    <bootstrappers>
      <currentbuildstatusbootstrapper
        file="/opt/build.ecf/logs/ecf/ECFcurrentbuildstatus.txt" />
    </bootstrappers>

    <modificationset quietperiod="600">
      <cvs localworkingcopy="/home/ted/workanon/org.eclipse.ecf/plugins" />
    </modificationset>

    <schedule interval="600">
      <ant buildfile="cc-build.xml" target="ecf.build" />
    </schedule>

    <log dir="/opt/build.ecf/logs/ecf">
       <merge dir="/opt/build.ecf/logs/ecf/test-results" />
    </log>
   </project>
</cruisecontrol>
```

Anyone want to help an old befuddled guy?
 -ted

---

### Post by tedk on 2007-05-21
The Pragmatic Programming book I was looking at does not have the right
syntax for the override.properties file. It says to give the name of the
logs directory which for me is /opt/build.ecf/logs. I started to see
results when I entered /opt/build.ecf/logs/ (note the trailing /).

This was after reinstalling just about everything. Sigh ... 

Began to learn more about the JMX console for cruisecontrol which (although powerful) has
the most abstruse user interface I've come across in a long time.

-ted

---

