---
title: "Can't Get Sound to Work"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by jptablakeman1 on 2008-03-11
I can't get sound to work and really have no idea where to start. Running lspci, I get the following information:

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)

I assume the modem and sound card are combined.

Any help would be GREATLY appreciated. I've spent 3 days searching the internet and nothing I've found makes sense to me, nor do they work.

I apologize if I've missed something and if this question is a waste of time. 

Thanks in advance....

---

### Post by freebios on 2008-03-11
hey try the dvd 32 bit installer it had a driver that worked for me. even though the drivers on the cd iso and dvd are supposed to be the same. its an option hope it helps.

---

### Post by superprash2003 on 2008-03-11
this might help [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by /usr/bin/hacked? on 2008-03-11
try installing the backports for gutsy. I can't find the code for it, but it goes: sudo apt-get install <gutsy-backports-something-or-other>

---

### Post by Adam3nt on 2008-03-11
I have the same problem and i tryed all the option nothing could i get the driver reinstalled??

---

### Post by nothingspecial on 2008-03-12
This is how I got my sound working. Hope it helps.

1st - sudo apt-get install linux-backports-modules-generic
 
2nd - Follow this thread 
[http://ubuntuforums.org/showthread.php?t=568463&highlight=toshiba+sound](http://ubuntuforums.org/showthread.php?t=568463&highlight=toshiba+sound)

[B]IMPORTANT
[/B]
These instructions were kindly posted when the latsest alsa was 1.0.15
Now the latest version is 1.0.16
If you download the latest alsa files and copy and paste the code in that thread, it won`t work. Make sure you change any line of code with 1.0.15 in it to 1.0.16

Hope it works :)

---

