---
title: "Beginner absolutely lost"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by ngiovas on 2006-05-23
Well, I hate to start off this way, but I need some assistance.  I have been digging through the forum and have found some tips, but haven't been able to resolve my issue.

I recently decided to take the plunge and try out Linux.  I first decided to go with Debian.  I struggled trying to get the PC I was going to load it onto to boot from the Debian CD.  I finally ended up making a boot floppy (actually 3) that allowed me to load the basics and then ftp the remaining files to do the final load (desktop configuration).

From there I was able to complete some basic configuration, but after further reading, I decided that I wanted to switch to Ubuntu before I got to far into the switch.  I started in the same manor with a CD image, but still wasn't able to get the system to boot from the CD (I burned an image of the CD using both Nero and Power ISO).  I finally made a boot CD using SBM.  I am able to get SBM to load, but it gives me an error when I try to select the CD drive.

Does anyone have any advice for me?  I can't seem to boot from CD (I have tried selecting boot from CD in the BIOS) and I can't seem to get the CD to work using the boot manager.  Is there a boot floppy similar to Debian that allows you to go strait into the load and then complete it via the net?  Once I did this with Debian I had no problems accessing the CD drive.

Any help would be greatly appreciated.

NG

---

### Post by tkjacobsen on 2006-05-23
If your computer can boot from usb, you can use this netboot installation boot image.

[http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/boot.img.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/boot.img.gz)

I don't exactly know how to get it on to an usb without using linux (I know it is possible in windows). But if you are using linux:

```
gunzip boot.img.gz
dd if=boot.img  of=/dev/sda
```
THIS IS IF /DEV/SDA is your usb device

The dd command should be run as root user or using sudo

---

### Post by ngiovas on 2006-05-23
Thanks, but unfortunately I don't have any way of booting from USB (no USB storage device).  There must be some way of getting it working since I was able to get the Debian to load on this PC.

---

### Post by richbarna on 2006-05-23
Hi ngiovas,
Judging by your problems, I would download another iso, make sure it is the correct one for your PC (386 iso) for example.
Oh yeah, is it a Laptop or Desktop ?
When you get the iso, right click on it and set the iso to open with Nero, that way when you double click it it will automatically burn correctly with the correct iso settings.
Also use a good make of blank cd ;)
In theory, if you have set the BIOS to boot from CD it should be ok.
Post back if you need any more help.

Also, if you get it to run, I would suggest doing the server install only and then adding the Desktop environment. This can sometimes cure any Graphic card problems.

You can also post here for a step by step walk through if you need anymore help :)

Welcome to Ubuntu Forums and 
Good Luck !

---

### Post by ngiovas on 2006-05-23
Thanks Richbarna.  I have a feeling it is the CD as well.  I tried sticking it in my primary PC which boots from other CDs fine and it won't load.  I can read the CD fine from both the Linux machine and the Win XP machine, but it just won't boot.  I will try and burn another copy at a slower speed and see if that helps.

NG

---

### Post by richbarna on 2006-05-23
Also remember that on the 1st JUNE Ubuntu Dapper will be available, I am using the test version and it is pretty awesome.
If you install Breezy now, you can upgrade later however.
Or download the Dapper iso for a fresh install.

Here is the Ubuntu 5.10 release ISO if you need it :-
[http://www.ubuntulinux.org/download]("http://www.ubuntulinux.org/download")
[http://distrowatch.com/?newsid=02988#0]("http://distrowatch.com/?newsid=02988#0")

---

### Post by christhemonkey on 2006-05-23
EDIT: Do not do this, you will get a broken system!

You could just stick with  debian, change repositories to ubuntu breezy, then apt-get update, apt-get dist-upgrade.

But then again that might just bugger everything up!

---

### Post by tkjacobsen on 2006-05-23
[QUOTE=christhemonkey]You could just stick with  debian, change repositories to ubuntu breezy, then apt-get update, apt-get dist-upgrade.

But then again that might just bugger everything up![/QUOTE]
This is not a good idea. Just because debian and ubuntu uses the same package system, doesn't mean they are compatible.. I wouldn't do this.. You will get a broken system..

Instead check this howto form wiki.ubuntu.com
[https://wiki.ubuntu.com/Installation/WithFloppies](https://wiki.ubuntu.com/Installation/WithFloppies)

or for other methods see::
[https://wiki.ubuntu.com/Installation/](https://wiki.ubuntu.com/Installation/)

---

### Post by ngiovas on 2006-05-23
tkjacobsen,

Thanks for the links.  I like the idea of starting with the debian boot disks (I used these for my Debian install) and then bootstrapping it to load Ubuntu.  I will give this a try tonight.

It seems like it would be much easier to get the SBM working and use the CD I made, but I still can't figure out how to get it to recognize the drive.  When I boot the debian OS, it recognizes the drive with no problems.  When I boot to SBM from the floppy it gives me an error.  Are there any settings within SBM to help it detect the CD drive?

NG

---

### Post by confused57 on 2006-05-23
I've used SBM and it always gives me an error the first couple of times I try it.
If I remember correctly, when the SBM menu comes up, press "F2", then "enter"...like I said, I usually have to repeat this 2 or 3 times to get it to finally work.

Repeat the steps while the menu is still showing, in other words, don't reboot.

---

### Post by ngiovas on 2006-05-23
Thanks to all who helped.  I ended up burning a new disk at 4x and then installed using SBM (after many tries).  Everything else went flawlessly.  I can certainly say that my first impression of ubuntu is very good.

NG

---

### Post by ed_agamemnon on 2006-05-23
in future you could try a net install...

here's an old version of some guides i wrote: [http://www.ubuntuforums.org/showthread.php?t=28948]("http://www.ubuntuforums.org/showthread.php?t=28948")

search around...

---

