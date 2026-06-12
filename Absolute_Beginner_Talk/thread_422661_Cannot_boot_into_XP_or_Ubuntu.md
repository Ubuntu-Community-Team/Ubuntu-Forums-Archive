---
title: "Cannot boot into XP or Ubuntu"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by gmc1200 on 2007-04-25
Hey everyone,

I have two hard drives: One for XP and the other for Ubuntu Edgy.  I just reinstalled Edgy because my Nvidia MX440 wasn't working in Feisty, so I decided to switch back (Edgy was perfectly fine before).  The way I have my computer set up is I unplug the XP hd when I install Ubuntu, so it doesn't add it to the Grub, that way I could just switch OSes by using the BIOS.  I just do this because it's my personal preference and I dont use XP all that often (or at least try not to).  

So I reinstalled edgy and did the basic updates, got my wireless going, Nvidia working, etc... During all of this, I had to reboot several times and it would boot into Ubuntu just fine.  I finally shut down my computer at the end of the day and the next morning I wanted to use XP because I had a torrent going that I wanted to finish.  So I boot up the computer, switch the drives in my BIOS, and rebooted.  The boot process goes all the way up to the splash screen (I think that's what it's called) but then it never makes it to the login screen.  The screen is just black as if the monitor isn't turned on.  I rebooted a couple times, but still no luck.

At this point, I figured it's no big deal so I just switch to my Ubuntu drive, but then the same thing happens.  When booting Ubuntu it doesn't even show the splash screen; it just displays a black screen as if the monitor's off.  I rebooted this a couple times and the same thing (I even tried unplugging the XP hd just to see if it was causing any issues, but the same thing happened).  I figured it might be my video card so I did Ctrl+Alt+F1, and I was able to get into the command line and did

```
sudo dpkg-reconfigure xserver-xorg
```

and I switched to the "nv" driver.  But it still didn't work.  I'm still a beginner at the whole Linux thing and I have no idea what went wrong because it was working perfectly fine yesterday.  Does anyone have an idea?

Thanks!:)

---

### Post by gary4gar on 2007-04-25
Please give the output of this from a live cd
>  fdisk -l

>  cat /etc/grub.conf

---

### Post by silverglade00 on 2007-04-25
Just a guess, sounds like when you plug in your XP drive, the hda and the hdb (or sda and sdb if you have that flavor) assignments get swapped. Wish I could help you fix it, but I have been stuck on single drive systems (laptops) for years.

---

### Post by gmc1200 on 2007-04-25
I can't get any output from fdisk -l (it doesn't do anything) or  cat /etc/grub.conf.  

If i just do fdisk i get this:

```
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

```

the latter gets me this 

```
cat: /etc/grub.conf: No such file or directory

```

I have a feeling that this isn't an Ubuntu issue because I tried reinstalling Ubuntu and I got the same boot problem as before.  I think it may be a hardware issue. Dammit.

---

### Post by gary4gar on 2007-04-26
[quote=gmc1200;2536061]I can't get any output from fdisk -l (it doesn't do anything) or  cat /etc/grub.conf.  

If i just do fdisk i get this:

```
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

```
u have to do "fdisk -**l**" not fdisk -**i**
```
cat: /etc/grub.conf: No such file or directory

```
try this ```
cat /boot/grub/grub.conf
```

---

