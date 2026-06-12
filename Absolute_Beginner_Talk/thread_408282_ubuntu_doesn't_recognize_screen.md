---
title: "ubuntu doesn't recognize screen"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by J_A on 2007-04-13
hi guys

I did try to run a search of the forum but it spat out nothing useful. forgive me if this has already been addressed. but I do need some help here.

I'm a total newbie to linux and was trying to install ubuntu 6.1. I burned an ISO disc from the ubuntu homepage and it seemed to start booting and installing but then hung itself up only showing the brown ubuntu screen (no progress). after retrying a couple of times, I tried to run ubuntu 5.1 from a live CD just to check if it'll work. 

it seemed to be mounting things but in the end it gave me a **"fatal server error: No screen found"**. also, the file **/dev/apm_bios **was missing. and in the end it said it couldn't enable the X server, that it was now disabled until the screen is configured correctly. only i don't really know what it wants me to do?...

it did ask once during the installation what kind of resolution it should use and i didn't change anything there, but I don't really know what else I could do?... is it advisable to wait for the 7.x release and try again? 

a friend told me it might be something with the Hz of the screen? that's not set correctly? :confused: 

help?

thanks :)

I'm currently running Win XP Pro, SP2 on a Dell Inspiron 6400 laptop, intel(R)core2 CPU; 1.83GHz, 2GB RAM, graphics card: ATI Mobility Radeon X1400 and have a partition of about 40GB ready for linux.

---

### Post by heimo on 2007-04-13
Yeah, this is probably one of the most common problems. And luckily, there's lots of tips and information how to fix it. It's best to start by running that part of the installation again, which asks for resolutions. This time you should try changing the settings, as it didn't configure your graphics card / monitor correctly. Hit ctrl+alt+F1 / F2 / F3 / F4 to change to virtual console, log in and follow this guide:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by J_A on 2007-04-13
kiitos ;-)

one other question though, what do you mean, "Hit ctrl+alt+F1 / F2 / F3 / F4 to change to virtual console" is that 'one of the F keys, whichever works'? i suppose so, excuse the question. and is that, during the installation?

---

### Post by justleen on 2007-04-13
you can hit any one of them.. they all should work.

They represent different terminals. You can have 6 at any time.. 
just use one, logon, and follow the instructions from there.

---

### Post by J_A on 2007-04-13
well, when I tried that (ctrl+alt+F1) it actually froze on me and went nowhere. seems I need to fix the res somehow first. 

so what I did again is try 5.1, this time the install disc, cause I thought, ok, I'll try and adjust the resolution. and then another question surfaced. I realized I wasn't sure which partition to tell linux to choose. obviously, they have different names in win and lin. so, i know my win is running on C, my data are on E and for linux I had assigned F. now, the partition sizes don't look the same when I look at them, so I couldn't decide. is there any way I can find out which is the correct partition (without bugging my boss)?

---

### Post by justleen on 2007-04-13
the first harddrivedrive is HDA, the second HDB etc.
the first partition on the first drive is HDA1, the second partition is HDA2 etc.

If your partions in created in that order as you say above, you linux partition should be HDA3

duroing the install you can choose " manually edit partition" . choose this option, and you will see  a graphical represantation of your drive. Your windows ones will be off type NTFS.
that way you can just make a not off which partitions to use (or NOT to use)

---

### Post by J_A on 2007-04-13
:) Thank you, I kinda thought so. On the other hand, what confused me is that some partitions seemed to be "logical" and others (like the win one) not. 

right now, all partitions are ntfs, so for linux, the assigned partition has to be reformatted. will it do it itself during the install or am I better off reformatting it manually prior?

---

### Post by justleen on 2007-04-13
the setup will format them  (the next screen will ask which partitions hsould be formatted)

as to logical drives: a drive can contain only 4 logical partitions. If you need more partitions then 4, an Extended partition is created.  In its turn, an extended partition can hold 4 partitions.
Windows has a nack of create extended drives, for some reason..

you shouldnt worry about it, unless you need more then for partitions..

---

### Post by J_A on 2007-04-23
well, I've waited for 7.0 to come out, and the laptop still isn't working, it throws me to the command prompt. but it's working on the desktop and so far I really like it! I'm playing around with it and enjoying. 

Might try knoppix on the laptop instead. we'll see.

---

