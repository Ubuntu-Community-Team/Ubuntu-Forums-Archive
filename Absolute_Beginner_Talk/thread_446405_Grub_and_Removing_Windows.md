---
title: "Grub and Removing Windows"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by PMatt on 2007-05-16
So I'm running into some trouble dual booting Windows (internal hdd) and Ubuntu (external hdd). I've made a few other posts on here to try and help with the error 21 message but nothing really worked (and some things seemed to be more trouble than it was worth).

I was thinking that I could just install Ubuntu onto the internal hdd and just run it off there. I'm not sure how this might conflict with the external hdd that has Ubuntu on it already (I'd like to just have the external as storage). I also want to make sure this would fix the problems I've been having with Grub (error 21: disk not found). What do you guys think?

---

### Post by confused57 on 2007-05-16
> **PMatt said:**
> So I'm running into some trouble dual booting Windows (internal hdd) and Ubuntu (external hdd). I've made a few other posts on here to try and help with the error 21 message but nothing really worked (and some things seemed to be more trouble than it was worth).

I was thinking that I could just install Ubuntu onto the internal hdd and just run it off there. I'm not sure how this might conflict with the external hdd that has Ubuntu on it already (I'd like to just have the external as storage). I also want to make sure this would fix the problems I've been having with Grub (error 21: disk not found). What do you guys think?

It shouldn't be any problem at all...the new Ubuntu install on the internal hard drive should install it's grub IPL code to the internal hard drive's mbr, overwriting the grub installed from your external drive's Ubuntu.

Added:  Might be a good idea to disconnect the external hard drive when you install Ubuntu to your internal hard drive...Are you able to restore Window's IPL code to the internal hard drive mbr?:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
or using the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If you can restore booting to Windows, it would probably be a good idea to defrag your Windows before installing Ubuntu.

---

### Post by nicepants on 2007-05-16
i think that nuking windows (or just dual-booting) and putting ubuntu on your internal would fix your problem, though i'm not sure if it would conflict with ubuntu on your external... is grub installed to the mbr of your internal hdd? if so, i would think the installer will just pick up the installation on your external so you can pick which one to boot - up to you if that's what you want to do, or if you just want to backup your /home and whatever else, nuke everything, and start from scratch.

i can't say either way if that's going to fix your problem with grub, then again i always keep my os's on one drive  and have never had any issues with grub.

i just re-did my whole hdd/partition scheme last night, and it looks like sweeping system changes should be a lot easier now. i have two hdd's that are purely storage, one primary partition for each hdd. my "main" hdd has two primary partitions, the first for (x)ubuntu, the second for windows, and then an extended partition containing partitions for swap, my /home, and two others for other linux distro's. this way all my settings get kept if something crazy happens to my linux partition and grub is installed on the mbr to boot up whichever os i choose.

hope some of that rambling helps! =)

---

### Post by PMatt on 2007-05-16
I'm pretty sure it's on the internal, but I don't really know how to check. The problem I've been having is that whenever I shut down and reboot, I get an error 21 message from Grub (the only way around it is to basically not shut down after an install). A lot of other people have this problem when they try and dual boot w/ ubuntu on an external hdd. I'm just trying to think of a simple way to fix it and this came to mind.

---

### Post by adrian15 on 2007-05-17
> **PMatt said:**
> I'm pretty sure it's on the internal, but I don't really know how to check. The problem I've been having is that whenever I shut down and reboot, I get an error 21 message from Grub (the only way around it is to basically not shut down after an install). A lot of other people have this problem when they try and dual boot w/ ubuntu on an external hdd. I'm just trying to think of a simple way to fix it and this came to mind.

Someone has a similar problem to yours and I think my explanation also explains your error 21 problems.

Enjoy:

[grub and linux in external hard disk explanation]("http://ubuntuforums.org/showpost.php?p=2670486&postcount=11")

adrian15

---

