---
title: "Installation problems-boot menu"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by shumboom on 2008-03-05
Hi

I have searched the forum but cannot find something similar to my problem.

I installed Ubuntu 7.10 on my Dell desktop pc and have never got it running becasue my boot.ini from windows always takes precedence on booting. Following some advice from the web I installed Supergrub into my boot.ini and hey presto I got the Ubuntu bootup menu.

Now only problem is nothing loads from the Linux menu at all, not even the windows. Everything gives file not found eg:

Booting Ubuntu...
root(hd0,1)
Filesystem type is NTFS
kernel /boot/vmlinuz-2.6.22-14-generic 0x7 root=UUID=b19dec9f-3dda-488e-820b-a56985 a232162 ro quiet splash
err 16 : file not found

Happily I still have windows so I can send this out but what can I do now?
Also I cant remember which partition I put Ubuntu on - how can I see this from windows (xp)?

thanks,Shumit

---

### Post by jken146 on 2008-03-05
It's not so easy to see the information in windows XP -- you'd be better off booting from a Ubuntu live CD.

Boot the live CD, then open a terminal and post the output of ```
sudo fdisk -l
```

---

### Post by shumboom on 2008-03-06
I just tried to boot from the live cd and surprisingly there are a whole host of i/o errors and it wont boot at all. Finally hangs trying to load some drivers. First time this has happened.

I am guessing my original installation was corrupt and now the cd tries to read/write some data from the original for some defaults. 

There appears to be nothing wrong with my windows so now I think all I want is my partition back - but I cant boot into linux so will some windows software reclaim it for me.

thanks,Shumit

---

### Post by mikeyphi on 2008-03-06
> **shumboom said:**
> I just tried to boot from the live cd and surprisingly there are a whole host of i/o errors and it wont boot at all. Finally hangs trying to load some drivers. First time this has happened.

I am guessing my original installation was corrupt and now the cd tries to read/write some data from the original for some defaults. 

There appears to be nothing wrong with my windows so now I think all I want is my partition back - but I cant boot into linux so will some windows software reclaim it for me.

thanks,Shumit

The LiveCD runs in RAM and does not interact with any OS on the hard drive. If the CD does not run properly then you probably have a corrupt CD.

If you have given up on Ubuntu and can easily boot into windows - you can use your windows to reclaim the disk space.

---

### Post by shumboom on 2008-03-06
The cd boots up fine on my second machine.

I dont want to give up with Ubuntu but I cant load it from the cd due to i/o errors so it must be looking for something that is not on the cd.


The machine is 2.8Ghz Dell and 2Gb of memory which has always been pretty reliable. The cd drive works fine too.
 

What else can I do?  thanks,Shumit

---

### Post by mikeyphi on 2008-03-06
Some computers do have problems with the LiveCD - the advice is to try the "Alternate" installCD
this is a text based installer and perhaps requires more interaction than the graphical installer - but nearly always works!!
Download and burn in the normal way.

---

### Post by shumboom on 2008-03-09
I was just trying the alternate cd and I got to the part where it was asking me where to put the partition. I want to put it in the same place as my original attempt but I am not sure where that is. I dont want to lose more disk space so I quit. 

 Im back to my old question of how to find out where I allocated disk space to Ubuntu - from windows. I think it was drive e but how can I be sure?

I suppose I could go for a meagre 10 gb partition this time and hopefully it will also pick up my original 80 as well. Is this a correct assumption?

Thanks,Shumit

---

