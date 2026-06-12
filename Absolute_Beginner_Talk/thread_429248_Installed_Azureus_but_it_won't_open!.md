---
title: "Installed Azureus but it won't open!"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by destructo on 2007-05-01
Hi there and thanks if you can help.

I have installed azureus and have java enabled this is the version i have.


java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)


When i click on the azureus icon on the desktop it opens then shuts down. I can't save any files with it or open torrent files with it. Its doing very little, any ideas?

Thanks.

---

### Post by Cynical on 2007-05-01
Try running azureus from a terminal and seeing what output you receive.

---

### Post by mahiyar on 2007-05-01
There could be quiet a few java versions floating around. If you feel java is the culprit (most of the times it is), use this command from CLI to select the correct version >> sudo update-alternatives --config java

---

### Post by destructo on 2007-05-01
Okay thanks for the suggestions. 

How do i run azureus from the terminal?

this is what i get, which one do i go with? 

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 

Thanks.

---

### Post by kelvin spratt on 2007-05-01
Azureus is not happy with the latest java format either go back to the last version or change the client
as i did the latest version  of ktorrent from their site is as good as they come i used the blue frog for years

---

### Post by jfinkels on 2007-05-01
To run azureus from a terminal, open a terminal and type ```
azureus
``` if it doesn't start, it will give you some error information as output in the terminal.

You might want to download the latest version of Azureus from their website, or you can try other, non-Java based torrent clients (like Deluge, Transmission, rTorrent, etc.)

---

### Post by mahiyar on 2007-05-01
I' am sorry, not at all skilled in java, versions and all. But what I did was I downloaded every possible java related download from Add-Remove (search java), then used the command given above to select.

BTW: Don't leave hope on Azureus its one of the best programme of its type out there

---

### Post by destructo on 2007-05-01
well i love the blue frog. i have been using it since 2004 i think and it is great. I got ktorrent and its going okay. I tried running azureus from the terminal but it does the same thing, it shuts down.
I will try installing as many java apps as possible. 

thanks for the suggestions.

---

### Post by kelvin spratt on 2007-05-01
as i said i'used the from for a long time but some version are better than others the last linux version done away
with safe peer to try and please the critics about resauces that was never an issue with me as it stop the bad data brigade as i'm not quite sure on wich dist i stopped using the the frog 3 weeks ago tried deluge etc then used ktorrent but that kept crashing updated from thier site to latest deb version all is fine 4 days on line no crashes setup to the same settings as the frog still using azur 1 in the router for port forwarding it fas ip filters
the same just not all the fancy bits and similler download speed ie often max out sorry can't help out more 
as i love the frog

---

### Post by richardjennings on 2007-05-01
i have had the same issue in the past with edgy. 

I am now running Fiesty. I installed azureus in synaptic. It is working perfectly for me now.



I'm guessing if you go ahead and press option 1) azureus will work for you. I have checked my working config. I am using /usr/bin/gij-wrapper-4.1

---

### Post by destructo on 2007-05-01
Wow it worked, azureus now stays open, now i need to test and see if it will download something.

I just typed in azureus in terminal after picking option 1 and it worked. 

Thanks a lot people.:guitar: 


I can't stand ktorrent personally but hey we all like different things.

Hopefully this will/may help other people.

---

### Post by sameer.india on 2008-03-30
I have the same problem and the java version is only one
/usr/bin/gij-4.2
when i start it from the terminal this is what happens
sameer@sameer-laptop:~$ azureus
DEBUG::Sun Mar 30 15:07:08 GMT+05:30 2008::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::145,ConfigurationManager::initialise::138,ConfigurationManager::getInstance::71,LoggerImpl::init::90,Logger::<clinit>::48,Class::initializeClass::-1,StartServer::<init>::70,Main::<init>::56,Main::main::162
changeLocale: *Default Language* != en (IN). Searching without country..
changeLocale: Searching for language en in *any* country..
changeLocale: no message properties for Locale 'en (IN)' (en_IN), using 'English (default)'
DEBUG::Sun Mar 30 15:07:10 GMT+05:30 2008::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,CryptoManagerImpl::<init>::73,CryptoManagerImpl::getSingleton::60,CryptoManagerFactory::getSingleton::33,AzureusCoreImpl::<init>::155,AzureusCoreImpl::create::92,AzureusCoreFactory::create::46,Main::<init>::143,Main::main::162
Aborted (core dumped)
sameer@sameer-laptop:~$

---

### Post by jingo811 on 2008-05-04
> **mahiyar said:**
> There could be quiet a few java versions floating around. If you feel java is the culprit (most of the times it is), use this command from CLI to select the correct version >> sudo update-alternatives --config java

I've switched over to Deluge 6 months ago since Azz or the Java part is never dependable.  But now I need to setup Azz to make some network comparisons.

_Questions:_
[LIST]
[*]How can I see what Java version numbers to put into the "version" part of this command?
[*]Also what file does this command write to?
[/LIST]

```

bill@gates:~$ **1.6.0-b105 >> sudo update-alternatives --config java**
[COLOR="Red"]bash: 1.6.0-b105: command not found[/COLOR]

```


```

bill@gates:~$ **azureus**
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Sun May 04 13:10:55 GMT+01:00 2008::com.aelitis.azureus.core.networkmanager.VirtualChannelSelector::select::272:
  Caught exception on selector.select() op: Operation not permitted
    NonBlockingReadWriteService$1::runSupport::80,AEThread::run::69
java.io.IOException: Operation not permitted
        at sun.nio.ch.EPollArrayWrapper.epollCtl(Native Method)
        at sun.nio.ch.EPollArrayWrapper.updateRegistrations(EPollArrayWrapper.java:202)
        at sun.nio.ch.EPollArrayWrapper.poll(EPollArrayWrapper.java:183)
        at sun.nio.ch.EPollSelectorImpl.doSelect(EPollSelectorImpl.java:65)
        at sun.nio.ch.SelectorImpl.lockAndDoSelect(SelectorImpl.java:69)
        at sun.nio.ch.SelectorImpl.select(SelectorImpl.java:80)
        at com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualChannelSelectorImpl.select(VirtualChannelSelectorImpl.java:446)
        at com.aelitis.azureus.core.networkmanager.VirtualChannelSelector.select(VirtualChannelSelector.java:272)
        at com.aelitis.azureus.core.clientmessageservice.impl.NonBlockingReadWriteService$1.runSupport(NonBlockingReadWriteService.java:80)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00000000, pid=10531, tid=3085163408
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# Problematic frame:
# C  0x00000000
#
# An error report file with more information is saved as hs_err_pid10531.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
bill@gates:~$ **version >> sudo update-alternatives --config java**
[COLOR="Red"]bash: version: command not found[/COLOR]

bill@gates:~$ **sudo version >> sudo update-alternatives --config java**
Password:
[COLOR="Red"]sudo: version: command not found[/COLOR]

```

---

### Post by mahiyar on 2008-05-04
Are you sure java is installed on your pc.

---

### Post by jingo811 on 2008-05-05
I've always installed Java from the Add/Remove menu and it worked with Azz some years ago.  Isn't this the proper way to setup Java for Azz?


[IMG]http://i29.tinypic.com/jf9s9c.png[/IMG]

---

