---
title: "Azareus How to Make it Work"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by durdensbuddy on 2008-01-19
Here's the problem I am having with Azareus.  I open through Apps -> Internet or through the docked launcher, the program will open for a second or two and then just disappears.  There are no errors to look up or anything.

I am running Ubuntu 7.10 amd 64.

---

### Post by bwhite82 on 2008-01-19
I haven't used Azureus for a while, but isn't it a java app? I would make sure that you have java installed and configured correctly. You could "sudo locate" the application and simply right click on it and click "open with java..." [Here's the Wiki page for java.]("https://help.ubuntu.com/community/Java")

---

### Post by philinux on 2008-01-19
Could be yesterdays updates it borked a few apps. Not sure if the fix is through.

[http://ubuntuforums.org/showthread.php?t=671137&highlight=azureus+disappears](http://ubuntuforums.org/showthread.php?t=671137&highlight=azureus+disappears)

---

### Post by durdensbuddy on 2008-01-19
I don't think it's yesterday's update that is causing me problems, or at least not the original problem I am going to post the error messages I got, hope that will assist in determining what I can do.

Typed "azureus into terminal"

shannon@shannon-desktop:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
DEBUG::Sat Jan 19 10:04:00 EST 2008  Data Missing /tmp/azupdater_1.8.3.zip
DEBUG::Sat Jan 19 10:04:02 EST 2008::org.gudy.azureus2.ui.swt.welcome.WelcomeWindow$3::runSupport::268:
    AEThread::run::69
org.gudy.azureus2.plugins.utils.resourcedownloader.ResourceDownloaderException: Error on connect for 'http://web.azureusplatform.com:80/az-web/releasenotes?version=2.5.0.4&locale=': 404 Not Found
        at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:486)
        at org.gudy.azureus2.ui.swt.welcome.WelcomeWindow$3.runSupport(WelcomeWindow.java:257)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002ad20950ae11, pid=12642, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# An error report file with more information is saved as:
# /home/shannon/.azureus/hs_err_pid12642.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)



Attempted to add java 

shannon@shannon-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

Truly a newb so all of this command line stuff really confuses/kinda frightens me.

---

### Post by clparker on 2008-01-19
pretty sure you just need to update the .jar file to the 2.5.0.4 file, worked for me, pretty sure that does it!

---

### Post by Ub1476 on 2008-01-19
I recommend [Deluge]("http://deluge-torrent.org/"):)

---

### Post by zolero on 2008-01-22
Hi guys!

It's really, really frustrating to read about such probs wth. Azureus. Have a look at [this post]("http://ubuntuforums.org/showthread.php?t=144546&highlight=install+azureus") and try with my packages. It works like a breeze for me. If this wasn't useful, try another client like qTorrent. I have built packages for this one too. Just ask me.  Good luck.  :rolleyes:

---

