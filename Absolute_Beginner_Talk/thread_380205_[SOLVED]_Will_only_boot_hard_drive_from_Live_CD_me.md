---
title: "[SOLVED] Will only boot hard drive from Live CD menu"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by wayfarer_boy on 2007-03-09
Hi

I recently bought my first intel machine (Evesham Voyager Pro C530), and immediately installed Edgy onto it.  It's been a bit of a struggle (having been a Mac user for many many years), but I'm really pleased as almost all of the components are working correctly - Beryl's doing its funky thing with the ATI card, the core duo chips are rattling away nicely in Blender, and my bluetooth key is busy sending images and audio files to my ericsson.

The trouble is, every time I boot up the machine (which isn't often), it doesn't recognise my hard drive as a bootable drive.  On starting up it shows the first intel screen (with F2 option for configuration - limited options there, nothing to help me out), then moves straight onto Intel Boot Agent, where it states that it cannot find any bootable volumes.  The only way I can get it to start up is to boot with the Ubuntu Live CD in the drive, allow it to load up the first menu, and choose the option to boot from the hard drive.

At that point, usually, the next screen to appear shows a single blank cursor.  I then power off (as there are no other options), power on again, let the Live CD boot to its menu, choose boot from hard drive, and GRUB then takes over - at this point, I know that Ubuntu will finally boot up, but it's such a pain to have to keep doing this (and to not be able to go anywhere without taking my Ubuntu live CD).

Does anyone have any ideas as to what I can do about this.  I've changed the boot order in my BIOS F2 configuration screen so that the hard drive is second only to the CD drive.  I've tried to disable the Intel Boot Agent, just in case it was taking over where it shouldn't - the trouble is, I've read that the IBA only comes on if the BIOS can't find a suitable bootable volume, so I figure it may be something else.

Any ideas?

---

### Post by chewearn on 2007-03-09
It is possible that your boot flag is not set.  You can use GParted to check and fix.

---

### Post by cyntek on 2007-03-09
Hi, I'm new to linux and I finished installing Ubuntu64bit w/ Winxp pro 32bit and I am also having the same issue where I can only boot from the Live CD once installed. Now, when i go to restart the winxp is the only one that boots up to login. I don't have the option to dual boot into Ubuntu. Why. I don't know. That is why I am here to find out. 

My configuration consist of : 

AMD Dual Core X2 4600+ 
Kingston HyperX Pc3200 400 2 Gig
160 GB Maxtor HD SataII
300 GB Seagate Baracuda Pata
500 GB Hitachi Deskstar SataII

---

### Post by chewearn on 2007-03-10
> **cyntek said:**
> Hi, I'm new to linux and I finished installing Ubuntu64bit w/ Winxp pro 32bit and I am also having the same issue where I can only boot from the Live CD once installed. Now, when i go to restart the winxp is the only one that boots up to login. I don't have the option to dual boot into Ubuntu. Why. I don't know. That is why I am here to find out. 

My configuration consist of : 

AMD Dual Core X2 4600+ 
Kingston HyperX Pc3200 400 2 Gig
160 GB Maxtor HD SataII
300 GB Seagate Baracuda Pata
500 GB Hitachi Deskstar SataII

Open up an terminal, please post output from the following:
```
df -h
cat /etc/fstab
cat /boot/grub/menu.lst

```

---

### Post by wayfarer_boy on 2007-03-10
Many thanks asta - didn't realise it was such an easy problem to solve!

For other noobs, a layman's howto:

[LIST]
[*]Enter 'sudo apt-get install gparted' in the terminal
[*]Launch gparted either from the terminal ('gksu gparted') or from the Main Menu -> System -> Administration -> GNOME Partition Editor
[*]Select your boot volume (mine was /boot, but yours may be /)
[*]Select Partition -> Manage flags
[*]Check the Boot flag
[*]Restart!
[/LIST]

Many many thanks again.

---

### Post by torgrot on 2007-03-10
Or easier yet at the GRUB screen tap "C" for the grub shell type find /boot/grub/stage1
you should get a response back such as (hd0,0)
type root (hd0,0)
type makeactive 
then reboot.

torgrot

---

