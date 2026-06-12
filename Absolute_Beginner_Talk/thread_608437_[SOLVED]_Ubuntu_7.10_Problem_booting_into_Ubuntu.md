---
title: "[SOLVED] Ubuntu 7.10 Problem booting into Ubuntu"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by rav26 on 2007-11-10
Hi,

I burned the Live CD that I downloaded from the website. I have a fresh Windows XP Professional SP2 installed on my hard drive. I put in the Live CD and it prompts me to restart my computer to boot from the CD. When I get to the Boot menu, I click on Start or install Ubuntu or Start Ubuntu in safe graphics mode, the splash screen comes up, and then the BusyBox comes up. 

At that point, I am stuck at the busybox and I don't know what to do after. Are there any commands I can type in to continue to boot into Ubuntu? 

Any help is appreciated, THANKS

rav26

*EDIT* When I try to do the Install in text mode, I get this message, "Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive. If so you can insert it and try again." 
And when I try again, it doesn't work. The Live CD is in my CD drive.

---

### Post by IamAcoconut on 2007-11-10
Weird stuff. I don't feel competent to judge on the causes - whether it's a compatibility issue, or a hardware problem, or whatever.

[LIST=1]
[*]Did you try the alternate CD?
[*]Did you use any other distros' liveCDs?
[/LIST]

I did use the alternate in order to be able to encrypt the entire '/' filesystem. Than had to disable quiet and splash options in /boot/grub/menu.lst - just in case you wanted to give it a try too. I've just heard of a tool enabling Windows to mount LUKS-encrypted volumes, haven't tested it though, I don't dual boot.

Cheers :-)

---

### Post by matthewcraig on 2007-11-10
Sounds like the CD is corrupted.  You can check the integrity from the boot menu when the CD boots.  Most likely you will have to burn a new CD.

---

### Post by rav26 on 2007-11-10
Okay problem solved. All I had to do was burn another copy. Thank you for the help, guys!

---

### Post by zabien1970 on 2007-11-10
rav26, under thread tools at the top of the page please mark this as solved

---

