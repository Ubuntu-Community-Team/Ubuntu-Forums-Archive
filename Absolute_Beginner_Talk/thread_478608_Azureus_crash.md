---
title: "Azureus crash"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Stickymaddness on 2007-06-19
Hi,

I was merrily using Azureus earlier, until it exited without any messages. I'd just changed a port on my router so I thought it was that, but now every time I run Azureus, it loads up fine, I can see the torrent I was downloading in the queue (even thought the torrent and its data is now gone) and then the application closes. I've tried all the obvious things I could think of, like re-installing, restarting my pc / router etc, but it hasn't helped. :(

Any help would be much appreciated!!

---

### Post by Crafty Kisses on 2007-06-19
> **Stickymaddness said:**
> Hi,

I was merrily using Azureus earlier, until it exited without any messages. I'd just changed a port on my router so I thought it was that, but now every time I run Azureus, it loads up fine, I can see the torrent I was downloading in the queue (even thought the torrent and its data is now gone) and then the application closes. I've tried all the obvious things I could think of, like re-installing, restarting my pc / router etc, but it hasn't helped. :(

Any help would be much appreciated!!

You might want to check what processes you have running at the time, it's possible that your CPU usage spikes up to 99%, so when you try to open that it crashes.

Go into terminal and type:
```
top
```
You can see what you have running, and what percent your usage is.

---

### Post by ferronica on 2007-06-19
why dont you use K-Torrent  it works very well in linux and have a nice settings for uploading and Q

---

### Post by angryfirelord on 2007-06-19
Type this in a terminal:
```
azureus
```
When it crashes, post the output.

---

### Post by Stickymaddness on 2007-06-19
> **angryfirelord said:**
> Type this in a terminal:
```
azureus
```
When it crashes, post the output.

```

changeLocale: *Default Language* != English (South Africa). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (South Africa)' (en_ZA), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=7898, tid=3084700560
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid7898.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted


```

[QUOTE=ferronica]why dont you use K-Torrent it works very well in linux and have a nice settings for uploading and Q[/QUOTE]

Hmm so I see! Thanks for this suggestion, I'm going to use this until I mange to get Azureus working again!

---

### Post by angelsneverdie on 2007-06-21
I'm experiencing the same problem.  I get this output:

changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  Internal Error (53484152454432554E54494D450E43505001A3), pid=7132, tid=3085153984
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_11-b03 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid7132.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)


anyone have any ideas?

ps  i've also tried reinstalling java to no avail

---

### Post by angelsneverdie on 2007-06-21
Open up your home folder, type CTRL+H to see the hidden files. Then open up your .azureus folder and delete your logs. Try to load it then. Should be all good

Hope this helps.


that worked for me - if it doesn't work long enough for me to get about it not working, i'll switch to a different app.

---

### Post by sra136 on 2007-06-21
Yo,
I had the same problem.  I deleted the log files and Azureus is working.  Thanks!

---

### Post by ehomo on 2007-06-26
> **angelsneverdie said:**
> Open up your home folder, type CTRL+H to see the hidden files. Then open up your .azureus folder and delete your logs. Try to load it then. Should be all good

Hope this helps.

that worked for me - if it doesn't work long enough for me to get about it not working, i'll switch to a different app.

how i can disable these logs?

---

### Post by SnakeHips on 2007-06-26
Hmmm ,I deleted the log files and it still wont run. gonna try a different app me thinks.


pete@myplace:~$ AZUREUS
bash: AZUREUS: command not found
pete@myplace:~$ azureus
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=6560, tid=3085208464
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid6560.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)
pete@myplace:~$

---

### Post by Stickymaddness on 2007-06-30
> **angelsneverdie said:**
> Open up your home folder, type CTRL+H to see the hidden files. Then open up your .azureus folder and delete your logs. Try to load it then. Should be all good

Hope this helps.


that worked for me - if it doesn't work long enough for me to get about it not working, i'll switch to a different app.

Awesomeness, thank you!

---

### Post by COKE CAN on 2007-08-08
I have tried the steps mentioned here and they have not worked.  I get the following:

```
thegoodpirate@laptop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Wed Aug 08 22:19:09 EDT 2007::org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl::download::516:
  Inconsistent stream length for 'http://192.168.1.250:2869/IGatewayDeviceDescDoc': expected = 3443, actual = 3444
    ResourceDownloaderURLImpl$2::runSupport::319,AEThread::run::69
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb4782172, pid=7007, tid=3084835728
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9172]
#
# An error report file with more information is saved as hs_err_pid7007.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

---

### Post by wormser on 2007-08-08
This [post]("http://ubuntuforums.org/showpost.php?p=1680674&postcount=13") resolved my issues.

> Go to [http://azureus.sourceforge.net](http://azureus.sourceforge.net) and download the newest jar.

Copy the downloaded jar file over your current Azureus2.jar (mine was located at /usr/share/java/Azureus2.jar

Open Azureus again and it should open without problems.

---

### Post by COKE CAN on 2007-08-09
> **wormser said:**
> This [post]("http://ubuntuforums.org/showpost.php?p=1680674&postcount=13") resolved my issues.

Tried this morning but only had mere minutes before leaving for work.  Found out I had to be su.  I will try tonight when I get home.

Thanks!

---

### Post by COKE CAN on 2007-08-09
I believe that it is fixed now!  

Thanks!

---

