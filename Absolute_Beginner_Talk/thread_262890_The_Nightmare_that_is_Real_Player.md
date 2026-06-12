---
title: "The Nightmare that is Real Player"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by Tobster on 2006-09-22
I tried so many times to down load Real Player.. I can't open the file to be able to write the command lines

Someone said about an alternative which I tried but it messed up my install manager so I had to re-install ubuntu

---

### Post by haxer on 2006-09-22
Try fix automatix!!

---

### Post by Omnios on 2006-09-22
Personally I used [B]Automatix to install realplayer and all my extra codecs, it even has mplayer and java intalled by scripts. 
[/B][http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)

 Though it takes the fun out of intallin I found it works.

---

### Post by slimdog360 on 2006-09-22
I have a feeling you can get it from synaptic. Perhaps this alternative was VLC as it plays everything under the sun, VLC I know is in the repositories.

---

### Post by ron999 on 2006-09-22
Hi Tobster
I too had a load of problems trying to install Real Player.
Eventually I used Automatix, I agree with haxer and Omnios.:D

---

### Post by nudnik on 2006-09-22
I>  tried so many times to down load Real Player.. I can't open the file to be able to write the command lines

Someone said about an alternative which I tried but it messed up my install manager so I had to re-install ubuntu

Download Real Player to your desktop.

If you have reinstalled Ubuntu, the terminal should be accessible from the Applications tab in the upper left hand corner of your desktop. Click on it, then Accessories, then Terminal.

If you succeed in opening the Terminal window, type after the command prompt;

cd Desktop
[ENTER]
chmod a+x RealPlayer10GOLD.bin
[ENTER]
./RealPlayer10GOLD.bin
[ENTER]

When the installer asks in which directory you would like Real Player installed, answer /usr/bin.  Simply answer affirmatively to all other requests and everything should go well.

---

