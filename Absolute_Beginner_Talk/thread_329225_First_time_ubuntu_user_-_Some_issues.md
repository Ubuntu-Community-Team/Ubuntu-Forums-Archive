---
title: "First time ubuntu user - Some issues"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by fsando on 2007-01-01
Hi
I have a few issues with my new ubuntu edgy (6.10).
Situation:
My machine: asus w1j, ati x1600, core 2 duo
System ubuntu edgy 6.10
Problem 1:
I had initially problems with my screen which were solved here: [http://www.ubuntuforums.org/showthread.php?t=325732]("http://www.ubuntuforums.org/showthread.php?t=325732")
Normal screen (gnome) looks correct. But the consoles (Ctrl+F1, F2 etc) look like colored snow, not even remotely recognizable.
Problem 2:
Strange Firefox problem 
Whenever I go to Digg spy [http://www.digg.com/spy]("http://www.digg.com/spy") 
 Xorg starts using 99% cpu and everything else slows down.
I have just installed swiftfox but it doesn't do anything to this problem. I have disabled javbascript - it only helps very little (probably because it stops the page from constantly reloading). The problem may be with firefox not ubuntu - perhaps the css rendering? I disabled css for Digg and Xorg dropped to around 20% to 50% (still slowing the rest of system). I haven't seen this behavior on other sites (yet?)
This is not an issue in windows.

---

### Post by Sef on 2007-01-01
With firefox, do you use any plugins? if so, what ones?   Some of them take up a lot of memory.

---

### Post by fsando on 2007-01-01
I disabled all extensions which appears to make things worse as I used 'web developer' to disable styles.
Xorg is now at 99% all of the time

---

### Post by fsando on 2007-01-01
The problem seems to be described here (Bugzilla):
[https://bugzilla.mozilla.org/show_bug.cgi?id=330605]("https://bugzilla.mozilla.org/show_bug.cgi?id=330605")
and here:
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/38131]("https://launchpad.net/distros/ubuntu/+source/firefox/+bug/38131")
It appears to be either a bug in Firefox or a problem with configuration of xorg related to the graphics-driver - if I understand it correctly.

---

