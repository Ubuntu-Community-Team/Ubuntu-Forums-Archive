---
title: "azureus?"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-06-08
so i tried azureus and the only time that it ran i loved it, but it this is what happened, i am also reporting a bug at the required location as this happens on both my computers.
here is the output if it is ubuntu related please tell me how to fix it please

ricky@ricky-desktop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
java.io.IOException: Connection refused
        at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.connect(AEClientService.java:129)
        at com.aelitis.azureus.core.clientmessageservice.impl.AEClientService.sendMessage(AEClientService.java:140)
        at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck(VersionCheckClient.java:238)
        at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo(VersionCheckClient.java:103)
        at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo(VersionCheckClient.java:87)
        at com.aelitis.azureus.core.versioncheck.VersionCheckClient.DHTEnableAllowed(VersionCheckClient.java:154)
        at com.aelitis.azureus.plugins.dht.DHTPlugin$13.runSupport(DHTPlugin.java:738)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=7098, tid=3084925840
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid7098.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)

---

### Post by Rocket2DMn on 2007-06-08
Not sure how to troubleshoot that off that top of my head, but it looks like Azureus could not connect because you don't have a location defined. 
Can you run Azureus from the Applications menu under Internet?  This should at least open a GUI for configuration.

---

### Post by NeoLithium on 2007-06-08
Have you tried running this command in a terminal? ```
sudo update-alternatives --config java
``` And select the Sun Java 6 option?

---

### Post by tito13kfm on 2007-06-08
I got a very similar error last night.  Azureus would seem to start but quit about a second after loadiing.  I was able to get it fixed by deleting the files from ~/.azureus/logs and ~/.azureus/tmp
I found the solution from another thread on these forums.

---

### Post by rickycodie on 2007-06-08
the java 6 idea didn't work thank though 

@tito where isthe thread? i've searched and haven't found anything?

---

### Post by fycloops on 2007-06-09
Thanks tito13kfm! I was having the same problem. Your fix solved it.

Fycloops:D:D:D:D

---

### Post by rickycodie on 2007-06-10
seriously where is this thread?  i really can't find it!

---

