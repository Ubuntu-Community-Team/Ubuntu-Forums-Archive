---
title: "Installation error: &quot;Failed to start X server&quot;"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by AlanDavidson on 2007-06-17
I have WinXP Home. I am trying to install Ubuntu 7.04 as dual-boot. I'm not a techie.

I downloaded and burnt the ISO according to the following instructions:
[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

I am installing according to the following instructions:
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

I used the option "Check CD for defects"

I then chose to install. I got the error:

"Failed to start the X server"

Can anyone please advise my next step?
.

---

### Post by RNAPro on 2007-06-17
I can't help you out much with this. I attempted a dual-boot once. Not only did Ubuntu not load afterwards, but neither did Windows. I have installed Ubuntu on a seperate hard drive. During the installation of Ubuntu I had the power to my Windows hard drive disconnected so that it would not be involved in any bootloader configuring by Ubuntu. After the install I shut the computer off reconnected the power to my Windows hard drive. I use my BIOS to select which hard drive I want my computer to boot to.

---

### Post by AlanDavidson on 2007-06-17
Note that Ubuntu is not yet on my hard drive. I am only running it from the CD. 

This option allows beginners like myself to browse around Ubuntu without actually installing anything. They call it a "live" session.
.

---

### Post by w4ett on 2007-06-17
Sounds like you might have to use the Alternate install CD.  What are your system Specs?  the live CD requires a minimum 256 MB Memory.

---

### Post by AlanDavidson on 2007-06-17
> **w4ett said:**
> What are your system Specs?  the live CD requires a minimum 256 MB Memory.

I have 2GB RAM.
.

---

### Post by jfdduge on 2007-06-17
Best guess is that this is video card related.  I had the same error on a laptop I was trying to run the Live version on.  What Video card do you have?

---

### Post by schorsch on 2007-06-17
What graphic card do you use?

---

### Post by AlanDavidson on 2007-06-17
> **schorsch said:**
> What graphic card do you use?

> **jfdduge said:**
> What Video card do you have?

I have 256MB ATI® Mobility™ Radeon® X1400 HyperMemory™ graphics card

Here is some extra info: 

When I used GParted to move my Windows partitions, I had best results with a "VESA" driver (I don't know what that is).

There is an old post on this forum:
[http://ubuntuforums.org/archive/index.php/t-80064.html](http://ubuntuforums.org/archive/index.php/t-80064.html)

RoshanDawrani says:

"If you are trying out Ubuntu 5.10 with a live CD, then instead of trying to modify the /etc/X11/xorg.conf to change the driver from default to 'vesa', you may enter the boot process in expert mode by entering 'live-expert' at the prompt at the start of boot process [don't press Enter to enter into the default mode]."

Maybe "vesa" is the key word. But I don't see any "expert mode" option in my version 7.04.
.

---

### Post by schorsch on 2007-06-17
There was a bug regarding the installation of Ubuntu on computers with ATI graphic cards ....

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

I do not know if it still exists on the actual CDs but it is worth a try .... and the link is up there in the sticky section, too ... ;)

---

