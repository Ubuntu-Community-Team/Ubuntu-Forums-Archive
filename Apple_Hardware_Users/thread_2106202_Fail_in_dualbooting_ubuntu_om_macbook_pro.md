---
title: "Fail in dualbooting ubuntu om macbook pro"
date: 2013-01-18
forum: Apple Hardware Users
---

### Post by hyalinus on 2013-01-18
Hi.
I'm the happy owner of a MacBook Pro mid 2010 as far as I remember.  Its running 10.7.xx. Latly it has been feeling slow and i have upgraded the RAM from 4 to 8 Gb. No luck and now I would like to run ubuntu for a more pleasent and fast experience. I'm new to ubuntu but want to explore.

I have followed the guide from:
[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I have given ubuntu 40 Gb of space.
I have been using the 32 bit ubuntu 12.10 distro. 
Is that okay or is there a special mac-hardware disto?

After i have completed the guid my problem is that ubuntu wont boot. The screen just freez after choosing ubuntu in the boot menu.
I have fixed the Partition Tables after the install.

I think the problems is that i have done something wrong in the installation proces.
Before install i have created a 4 Gb linux swap and a 36 Gb EXT4 partition.
I think a have set the EXT4 partition as root (/) but when i comes to installing the boot loader (grub) to the root Ubuntu partition im having problem. 
What does it mean? and how to i install the boot loader?
I think that ubuntu does not boot since the bootloader is not installled
Before installation im also prompt about som bios-partition i haven't created. Angain i don't understand the problem and therefore don't know how to fix it. Is the bios-partion the same at the bootloader?

It would bee nice if you could post at link to at picture guide as im new to ubuntu.

---

### Post by minsf on 2013-01-20
what do you get when it freezes? a blinking cursor? "GRUB"?

you probably want to use the amd64 iso, not the 32 bit.

you when the installer starts and ask you about the partition, there is a way to tell it where to install grub. you want it to be installed to /dev/sda3 or /dev/sda4 if i understand your partitions correctly. make sure you use refit to sync the partitions.

---

