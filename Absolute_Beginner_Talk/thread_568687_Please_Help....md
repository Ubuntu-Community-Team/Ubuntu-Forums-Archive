---
title: "Please Help..."
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by wakeupinflames on 2007-10-06
Hey, I'm new to Linux, and was just tired of Windows so decided to download the .iso and I burned it to a CD. Then I set it up to boot from the CD, and the menu comes up and I select on option that says something like "Run in Safe Mode" and then it starts a progress bar, and the bar freezes about a 5th of the way through and the CD stops spinning. Is it ment to do that? I left it up for like 4 hours because I heard that it takes a long time to load because it's reading it directly from the CD as opposed to the HDD but it didn't move at all. My specs are:

Windows Vista Ultimate
Compaq Presario 6000
Intel i845E/G Chipset
1528 Mg. of DDR
2.52 GHz

Am I doing something wrong? When I select the option to "Start or Install" a command prompt thing comes up and then shoots out like 1000 commands and then the disk stops reading. I've been looking around on this site trying to find something that pertains to my problem, but I can't seem to find anything. If someone has any idea as to what the problem is, I'd really appreciate it.

---

### Post by Sef on 2007-10-06
1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the iso download?

2) Did you burn the iso at 4x or less?  Faster can corrupt the burn.

3) Did you check the cd for errors?

---

### Post by Amazona aestiva on 2007-10-06
In the menu there is an option called "Check disc for defects" or something like this.

Have You tried it?

---

### Post by wakeupinflames on 2007-10-06
I burned it at 47x, but I checked it through the main menu of the installation and it said that there were no errors found.

---

### Post by candtalan on 2007-10-06
even with no errors found I would still burn again with at least half the rated speed, or less. An iso does not need much wrong and it will be vulnerable.

good luck

---

### Post by wakeupinflames on 2007-10-06
I just tried the MD5SUM and it says that the check sums are the same.

---

### Post by Amazona aestiva on 2007-10-06
> **wakeupinflames said:**
> I burned it at 47x, but I checked it through the main menu of the installation and it said that there were no errors found.

I think it is too fast for burning. I burn 16x.

Anyway I'm useless here. Sorry.

---

### Post by wakeupinflames on 2007-10-06
Alright, I'm going to burn it again. Thanks for the quick responses. I'm crossing my fingers.

---

### Post by wakeupinflames on 2007-10-06
Alright, I just wrote it at 7x (the slowest that I could) and it still did the same thing as before. Something I've noticed though is that when it's loading the Live CD version in Safe Mode, it acts like it's trying to read from the Floppy Disk Drive. Should I have a floppy in with some kind of file on it like drivers or something? I read through the instalation instructions but didn't see anything about that. I don't really know what else to try...anyone else got any ideas? Thanks.

---

### Post by wakeupinflames on 2007-10-06
Does anyone know anything else that I can try...like do you think that it might be my CD ROM drive or something? If so, is there anyway to boot from a Virtual CD ROM drive like DAEMON Tools? I'm just totally clueless.

---

### Post by hums07 on 2007-10-06
You can try Wubi installer [here]("http://wubi-installer.org/index.php"). It is a windows-based Ubuntu installer. If you have a spare of 6 GB disk space, Wubi can use it to install Ubuntu. Because you have downloaded the iso file, put the iso in the same folder with the installer (i.e. wubi.exe).

Good luck

---

### Post by n3tfury on 2007-10-06
> **wakeupinflames said:**
> 
Am I doing something wrong? When I select the option to "Start or Install" a command prompt thing comes up and then shoots out like 1000 commands and then the disk stops reading. I've been looking around on this site trying to find something that pertains to my problem, but I can't seem to find anything. If someone has any idea as to what the problem is, I'd really appreciate it.

this is going to sound like a pain in the *ss, but those error codes would help this forum figure out your problem.  also, you should mention which version of ubuntu you downloaded.

---

### Post by wakeupinflames on 2007-10-06
> **hums07 said:**
> You can try Wubi installer [here]("http://wubi-installer.org/index.php"). It is a windows-based Ubuntu installer. If you have a spare of 6 GB disk space, Wubi can use it to install Ubuntu. Because you have downloaded the iso file, put the iso in the same folder with the installer (i.e. wubi.exe).

Good luck

I'm going to try that, I was trying to install Fiesty Fawn. If this doesn't work I'll get the error codes and post them here. Thanks everyone.:grin:

---

