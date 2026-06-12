---
title: "installation issues can I update 6.0 to 7.0 without issues?"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Aishiko on 2007-08-24
I'm getting an error when installing Feisty Fawn I get an error (I can't remember which and I'm running Memcheck on that PC now) and I'm wondering if I use the 6.0 version if I can update it to 7?  

Specs you ask?

Tyran Tiger 133
1 gig (4 stiix of 256 eaches, at PC100)
30gig HDD no partation (it's a Quantum Fireball just recently cleaned off)
2 Intel 700 Mhz Bronzemine CPUs
Nividia MX440 32 or 64 MB (I can't recall which)
5 port USB 2 Interface Card
2 Ultra 66 Promise ATA expantion cards
a generic (IBM I believe) 10/100 ethernet card
Soundblaster Live 5.1 sound card
ohh and a Compaq branded oem DVD drive


Can any one tell me what I may be doing wrong at the moment it's just the 2 drives each as Master on their cable both are connected right to the motherboard which I think is ATA 100 or 133 speed rated.  I can run the Konppix Live CD... 

Right now I'm considering;
Bad ISO burn
bad RAM
some other unsupported piece of Hardware like a chipset
Hard drive and DVD drive are known good and working as is the Motherboard and CPUs, RAM was fine, but I'm checking it just to be sure.

any assistance would be nice, and thank you all for your time

Aishiko

---

### Post by ramjet_1953 on 2007-08-24
There is no definitive answer to your question.

Many people have no problems at all.

However, if you have installed third-party video drivers, wireless drivers, etc, you will probably need to re-install and configure them.

Also, if you have used AutoMatix to install packages, you may also run into grief.

Sorry that I can't be more positive, but there are so many variables.

For myself, I always back-up my home directory and do a fresh install, which can be far less painful.

As far as the problems you are having with your install disk, I'd double-check the MD5, to make sure it is OK. 

I have had problems in the past with low cost CDR's giving problems as well. I burnt an image, which checked out OK and the next day it was corrupt.

Regards,
Roger :cool:

---

### Post by Aishiko on 2007-08-24
well I have nothing to back up I can't get it to install and I've got Verbatim CD-Rs maybe I'll burn a new one but it seems to work fine to run the MemTest but I got the extra long command propmt thing when I tried to check the CD.

---

### Post by Aishiko on 2007-08-24
Thanks for your help, I'm not sure what the issue is I'm downloading it again from a different mirror and I'll try burning it again.  I'm tired of Windows dying in me in the middle of an operation.

However, I have saved the Hard drive with my windows install on it so I can put it back into the system if I have to, to have a working computer again.

Aishiko

---

### Post by ramjet_1953 on 2007-08-24
Another thing that you could try is to download the Alternate CD.

This is a text based installer which often succeeds, when the LiveCD doesn't.

Even though it is text based, it is quite intuitive and you shouldn't have any problems.

Regards,
Roger :cool:

---

### Post by Aishiko on 2007-08-24
I'll download that as well and burn it as well if the new Live CD doesn't work I'll try the Alt CD.

and I'm hoping that I can get it up and running tonight... AKA I won't rest until Ubuntu is working on that PC!  (or I collaspe from exhaustion which ever comes first.)

also I'm thinking of a 10ish "/", a 2ish "swap" and the rest in "home"  what do you think?

regards,
Aishiko (current status: tired, frustrated, and hating M$ more then the Linux install problem(s))

:D

---

### Post by Mud.Knee.Havoc on 2007-08-25
Sounds like an error on the disc... although you say you can't even get through burning a disc in Windows without it locking up on you?  If so, I'd say you've got bigger problems.

Best thing to do is check the md5sum on the iso, since that's usually the culprit.

---

### Post by Aishiko on 2007-08-25
ummmm no I don't have a burner in that computer the other computer the one I'm on now has the Burner and it does OK so far hasn't crashed but it's normally used by a lightwieght computer user and it doesn't have all the programs I use.

Sad thing is my windows computer was fine until a couple weeks ago and now it's crashing, rebooting, locking up, or blue screening on me sometimes as much as 6 times a day.  It's been a bit of a pain since day one.  But then it is Sever2003.

---

### Post by Aishiko on 2007-08-25
OK the text based one is working, now if I can only get it to recognize my Ethernet card(s) I only want one I have I don't know it's brand and then I have 2 SMC, and a 3Com all PCI

---

### Post by Aishiko on 2007-08-25
OK I have a supported ethernetcard that is not being detected (The unknown turned out to be a SMC 1244TX) but the chipset is;
RTL8139C
14190A1
not;
8139too  
anyone Have any ideas?  In the meantime I'm going to see if I can find any other Ethernet cards in my mis/old hardware collection.

---

### Post by igknighted on 2007-08-25
You are using 6.06?  Did you install a kernel with SMP support?  IIRC you need to install a dual core/dual processor kernel in order to make use of both CPUs.  This was changed in 6.10 and later, so the stock kernel supports the use of both CPUs.

BTW... Dapper = 6.06 because it was released in the 6th month (june) of 2006.  Edgy = 6.10 because it was october 2006, feisty (7.04) april 2007 and so on.  So "6.0" and "7.0" aren't really releases, because the 6 and 7 do not stand for major version changes like most software, merely the date released.

---

### Post by Aishiko on 2007-08-25
So far I've not gotten past the network part of the process as I stop (ctl+alt+del) and try a different card out of the 7 in hte house I can find not one is supported :(
break down 4 SMC, 1 3com, 1 netgear, and 1 linksys.
The Linksys is next up but the SMCs, and the 3com didn't work they wern't even detected :(

---

### Post by Aishiko on 2007-08-25
Update:

I've got Ubuntu installed but it hangs on boot up and I get a busybox error and can't find /bin/sh/

Anyone seen this before?

while I see what responses I get I'm going to see what information I can find if I find anything on how to fix it I'll share it here.

---

### Post by Aishiko on 2007-08-25
the only thing I've found so far is using the 6.06 Live CD booted perfectly so I guess something major changed when it moved from 6.06 to 7.04  I've been reading it ming be the kernel revisoin from 2.6.20 from 2.6.15.

On thgat note can I upgrade to 7.04 but not upgrade the kernel?

---

### Post by Aishiko on 2007-08-25
> **igknighted said:**
> You are using 6.06?  Did you install a kernel with SMP support?  IIRC you need to install a dual core/dual processor kernel in order to make use of both CPUs.  This was changed in 6.10 and later, so the stock kernel supports the use of both CPUs.

BTW... Dapper = 6.06 because it was released in the 6th month (june) of 2006.  Edgy = 6.10 because it was october 2006, feisty (7.04) april 2007 and so on.  So "6.0" and "7.0" aren't really releases, because the 6 and 7 do not stand for major version changes like most software, merely the date released.

I'm trying to see if SMP is turned on or even how to turn it on the other thing I need help with is geting the ethernet card, sound card and the USB, on hte computer working, I need to know how to add hardware because it doesn't appear to be auto detected.

---

