---
title: "Problem With Installation (X-Server)"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by arky2000 on 2006-06-12
Hello Everybody!

Long story:
======
I am new to Linux; Although I have always wanted to give it a go, i have been studying hard for my economics degree so there has been no time to experiment with the Fedora Core 4 that i installed. However, now that i have finished i have all the time in the world to play around with linux. I am a PHP programmer, and I generally love learning new things. However, there are a few things that have been bothering me with Fedora, the most particular being that the Red Hat Auto update never works and always hangs.
I have managed to get it to access the internet,  play MP3, mount NTFS partitions etc, go me! hahah :p  However, i have read a lot of the debates about Ubuntu being better, and without going into specifics, the majority of the comments are favourable towards Ubuntu.


My relevant system specs are:
AMD ATHLON 64bt 3700
2 x 200gb SATA hdd's

HD1 > WinXP/NTFS
HD2 > Partition 1: 180gb NTFS 
        Parition 2: 9gb Partition, with Fedora installed onto it
ATI Radeon x800 GT

Short Story
=====
I downloaded the latest version of Ubuntu (6.06 64bit) and put it onto a CD (i did however burn it at full speed, but the ubuntu installation screen there's a CD check and that reported everything as ok). Now when i try to install it, it loads up a few things first, but then the screen changes to a blue one (talk about the BSOD!) with funny characters and the message "Failed to start x server"...please edit the configuration manually. And thats it. 


Does anybody have any idea how to fix this? I would be ever so greatful. I have googled for this problem, and searched the forums, but all the x-server problems are not relevant to mine.

Thank you in advance!

---

### Post by Blondie on 2006-06-12
Maybe this will help,

[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

---

### Post by arky2000 on 2006-06-12
thank you Blondie, but doesnt that thread only help with issues that occur after installation?

---

### Post by Tido on 2006-06-12
Which one did you download ?

1. "Desktop CD" includes a Live-CD and comes with a graphical installer 

2. "Alternate install CD" this is a Text-Based installer but offers you more possibilities

---

### Post by Blondie on 2006-06-12
Well I would try it anyway, THEN tell me it doesn't work :D 

You could go on to the end of the install and work from there. Surely a reinstall is not a big deal if you can't get the first install to work anyway :confused:

---

### Post by Blondie on 2006-06-12
Just to get things clear, when the "blue" screen comes up is there no menu from which to make choices whatsoever? I've seen this happen but with a yes / no choice with the keyboard keys. Please describe exactly what happens.

---

### Post by catlett on 2006-06-12
I hate to say it but if you have an ATI card good luck. There are tons of people in the forum with ati issues. That is your issue, the automatic configuring of your video card isn't working. That's why it is saying to ".please edit the configuration manually"
Are you trying the live cd out? Are you running the installer?
I wouldn't install until you solve this using the live cd.
 What does your Fedora configuration look like? I would go into Fedora and call up your X configuration and copy it. Then I would use that configuration in Ubuntu.
If you get to a command line in Ubuntu run```
 sudo dpkg-reconfigure xserver-xorg
``` that lets you set up the xserver manualy. Good luck with that ATI card. (I would google ubuntu and ATI Radeon x800 GT and see what you get)

---

### Post by arky2000 on 2006-06-14
thank you all for your incredibly helpful responses, i'll be trying out the suggestions, with the easiest first :)

*googles ubuntu and ati...."

---

