---
title: "Problem running Ubuntu of Compaq Presario"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Imashinu on 2007-05-28
First off here are my system specs,

```
-Compaq Presario SN134NX
 -250GB HDD -150GB HDD
 -Processor: AMD Athlon 64 3500+, MMX, 3Dnow, ~2.2GHz 
-Memory: 1470MB -Graphics: ATI Radeon Express 200, 256MB 
```

Thats not the best format but if you need anymore info just ask.


I burned the ISO to the disk, after performing a MD5 check.

The disk loaded on boot-up with no problems. I selected to load it as live CD so I could see how it would run. The loading screen came up and it ran for a few minutes and I get this error...


```

Busybox v1.1.3(Debian 1:1.1.3-3ubuntu3) Built-in Shell (ash)
 Enter 'help' for a list of built in commands.

 /bin/sh: Can't access tty; Job Control turned off
```



If anyone can help me out, it would be great.

---

### Post by Lucifiel on 2007-05-28
Well, we kinda need your full system specs like what make of motherboard you have. I can't seem to find your computer model on the internet. Could you please double-check your model? 

If I'm not wrong, this could be connected to loading of certain hardware devices when running the Livecd but without your hardware info, it'll be quite hard to pinpoint the issue.

---

### Post by Imashinu on 2007-05-28
Thats my fault, the PC make is Compaq Presario SR1834NX

Here is the full spec page,
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&lc=en&cc=us&dlc=en&product=1841851&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&lc=en&cc=us&dlc=en&product=1841851&lang=en)

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00609393&lc=en&cc=us&dlc=en&product=1841851&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00609393&lc=en&cc=us&dlc=en&product=1841851&lang=en) (full specs)

---

### Post by Lucifiel on 2007-05-28
I'm really sorry for taking my time to respond. I'm still trying to find a solution to your issue. :)

---

### Post by Imashinu on 2007-05-28
I appreciate the help man :)

---

### Post by Imashinu on 2007-05-29
Sorry for bumping but I could really use help on this.

---

### Post by Lucifiel on 2007-05-29
Sorry... I found a thread relating to this issue but it is really long and there are many solutions listed. However, some those solutions work only for some but not others. And many of the solutions are very complicated and I've no idea how to implement them. They require extensive knowledge of Linux and I've started using Linux for only 2 months. :(

I'll explain: the tty message you get is displayed whenever you get an error(hardware or software) so I can't use my usual way of backtracking the issue. 

Well, you could read the thread if you want but, I think there are a few "real easy" solutions you could try:

a) If you can, disable your floppy drive from the BIOS and boot the LiveCd. 

b) If you have 2 dvd/cd-drom drives, disable one of your dvd drives from either the BIOS or disconnect one of them. (I know that some BIOS versions allow you to disable your IDE controllers.) 

c) If you have 2 hard disks, you can disable one of them. Again, it's likely you can disable them from the BIOS. 

To enter BIOS, you'll need to check the manual which key you should use. For mine, I use F1 and for another's laptop, I use Delete to access it.

And after you've set up everything, make sure to enable everything again!! :p 

Here's the thread if you care to give a read through it:
[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

Sorry I can't help more. I hope someone else can come in and help you. I won't be around for perhaps a few days 'cos my hard disk is failing.

---

### Post by Imashinu on 2007-05-29
Figures that its something stupid. I'll spend some time after work tweaking with the hardware. I really appreciate your time and speedy results. Thank man, I hope this fixes it.

---

### Post by Lucifiel on 2007-05-29
Well, I hope it all works out for you. :)

---

### Post by Imashinu on 2007-05-29
Ya all of their solution ideas failed. I'm going to install freespire for now and upgrade to ubuntu when they fix this bug.

---

### Post by Lucifiel on 2007-05-29
> **Imashinu said:**
> Ya all of their solution ideas failed. I'm going to install freespire for now and upgrade to ubuntu when they fix this bug.

Yeah, that's a better idea for now. Or perhaps you could give PCLinuxOS a shot if you dislike Freespire. 

I hope to see you around in maybe a few months' time. :) I think that by then Gutsy should be released. 


Good luck! :D 

Lucifiel

---

### Post by Hendrick on 2007-05-30
> **Imashinu said:**
> Thats my fault, the PC make is Compaq Presario SR1834NX

Here is the full spec page,
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&lc=en&cc=us&dlc=en&product=1841851&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&lc=en&cc=us&dlc=en&product=1841851&lang=en)

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00609393&lc=en&cc=us&dlc=en&product=1841851&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00609393&lc=en&cc=us&dlc=en&product=1841851&lang=en) (full specs)

Hey

I have a Compaq Presario SR1620NX.  I have the exact same issue.  However... it only appeared when I updated Ubuntu, with the newest update.  I would suggest to reinstall it, and not run the updates.

PCLinuxOS refused to work for my internet for WEP.  But the same card works fine on Ubuntu.

---

### Post by Lucifiel on 2007-05-30
> **Hendrick said:**
> Hey

I have a Compaq Presario SR1620NX.  I have the exact same issue.  However... it only appeared when I updated Ubuntu, with the newest update.  I would suggest to reinstall it, and not run the updates.

PCLinuxOS refused to work for my internet for WEP.  But the same card works fine on Ubuntu.
Given that the original poster couldn't even run the Ubuntu livecd, I don't think he ever got to install Ubuntu.

---

### Post by Hendrick on 2007-05-30
Could the CD possibly already have that update on it?  If thats the case, he would have to find an older version of the CD (Mines about two weeks old, and it's fine.)

---

