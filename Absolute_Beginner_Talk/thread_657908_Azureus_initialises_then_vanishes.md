---
title: "Azureus initialises then vanishes"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by MeanStreak on 2008-01-04
Azureus has been installed via apt-get, it appears under Applications > Internet. I click and it starts up, splash screen shows initialising main window then WHAM - it vanishes - Alt-Tab does not show it running. Any ideas?

---

### Post by kpkeerthi on 2008-01-04
Start it from the terminal. You may find something useful printed in the console.

---

### Post by MeanStreak on 2008-01-04
Good advice. Although I'm a terminal noob - what's the command?

---

### Post by kpkeerthi on 2008-01-04
I dont use azureus. Type **azu** and press tab (twice if nothing prints)

---

### Post by conehead77 on 2008-01-04
Under ~/.azureus/ there is a folder called "log" or sthg like that. Delete the content of that folder and start azureus again.

---

### Post by MeanStreak on 2008-01-04
In the root filesystem? I'm having trouble locating that directory.

---

### Post by RomeReactor on 2008-01-04
Hi. To run Azureus from the terminal:
```
azureus
```
Installing **azurues-gcj** helps:
```
sudo apt-get install azureus-gcj
```
Also, from the terminal, try deleting the logs:
```
rm -R ~/.azureus/logs
```
then start Azureus again. If the version in the repositories keeps having problems; you may want to try [downloading version 3 from their site]("http://azureus.sourceforge.net/download.php"); it's very stable.

---

### Post by conehead77 on 2008-01-04
> **MeanStreak said:**
> In the root filesystem? I'm having trouble locating that directory.

In the home directory. Its a hidden file. If you press ctrl-h in nautilus you can see the hidden files.

EDIT: poster above described how to delete the logs :)

---

### Post by MeanStreak on 2008-01-04
Result from running Azureus in the terminal:

```
charles@charles-desktop:~$ azureus
DEBUG::Fri Jan 04 20:36:17 EST 2008  Data Missing /home/charles/Desktop/John Mayer/John Mayer - Continuum (2006)
java.io.IOException: Connection refused
        at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.connect(AEClientService.java:129)
        at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.sendMessage(AEClientService.java:140)
        at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck(VersionCheckClient.java:238)
        at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo(VersionCheckClient.java:103)
        at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getExternalIpAddress(VersionCheckClient.java:138)
        at com.aelitis.azureus.core.instancemanager.impl.AZMyInstanceImpl.readExternalAddress(AZMyInstanceImpl.java:207)
        at com.aelitis.azureus.core.instancemanager.impl.AZMyInstanceImpl.getExternalAddress(AZMyInstanceImpl.java:336)
        at com.aelitis.azureus.core.instancemanager.impl.AZInstanceImpl.encode(AZInstanceImpl.java:47)
        at com.aelitis.azureus.core.instancemanager.impl.AZInstanceManagerImpl.sendMessage(AZInstanceManagerImpl.java:348)
        at com.aelitis.azureus.core.instancemanager.impl.AZInstanceManagerImpl.sendMessage(AZInstanceManagerImpl.java:330)
        at com.aelitis.azureus.core.instancemanager.impl.AZInstanceManagerImpl$request.<init>(AZInstanceManagerImpl.java:1213)
        at com.aelitis.azureus.core.instancemanager.impl.AZInstanceManagerImpl.sendRequest(AZInstanceManagerImpl.java:1172)
        at com.aelitis.azureus.core.instancemanager.impl.AZInstanceManagerImpl.search(AZInstanceManagerImpl.java:661)
        at com.aelitis.azureus.core.instancemanager.impl.AZInstanceManagerImpl$4.runSupport(AZInstanceManagerImpl.java:241)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E4350500214), pid=8697, tid=3085159312
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid8697.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
charles@charles-desktop:~$ 


```

---

### Post by MeanStreak on 2008-01-04
Deleting the logs did the trick - thanks to all of you - a credit to the Ubuntu community.

---

### Post by conehead77 on 2008-01-04
> **MeanStreak said:**
> Deleting the logs did the trick - thanks to all of you - a credit to the Ubuntu community.

I think its a known bug and happens when azureus crashes, so be prepared to do this again.

I switched to deluge anyway :)

glad we could help :)

---

### Post by RomeReactor on 2008-01-04
Have you installed azureus-gcj? Give version 3 from their site a try.

EDIT: Posted late.

---

### Post by MeanStreak on 2008-01-04
> **RomeReactor said:**
> Have you installed azureus-gcj? Give version 3 from their site a try.

Yes, I have installed azureus-gcj but still experiencing regular failure, requiring a regular log deletion to resume. I will try Deluge. Why did this version get released to the repository with such a glaring bug?

---

### Post by RomeReactor on 2008-01-04
> **MeanStreak said:**
> Yes, I have installed azureus-gcj but still experiencing regular failure, requiring a regular log deletion to resume. I will try Deluge. Why did this version get released to the repository with such a glaring bug?

Good question; it's been like that since Edgy, I think. If you still want Azureus, then version 3 will work very well (though it will still consume a lot of RAM, as usual). If using Azureus is not a necessity, then Deluge is great.

---

### Post by Digitallysick on 2008-01-04
I switched to ktorrent, you will find its a lot like utorrent and very fast, check it out as well

---

