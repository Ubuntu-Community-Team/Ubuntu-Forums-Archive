---
title: "Installing on a no CD no floppy system"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by bem202 on 2007-11-20
I am trying to install ubuntu on a toshiba portege 3480CT with no cdrom or floppy. It also will not boot to usb drive. It also has no ethernet port. BUT I do have the ability to rip the HD out of the sucker and put it in a usb HD caddy which I can then attach to my desktop.  I have tried installing the live and alternate cd's to it via the desktop BUT when I put it back into the toshiba it doesn't boot. 

It has 192mb of ram and a 20gig hard drive. I am considering Xubuntu but have run into the same problem there. 

Any ideas. I think installing to the HD via the alternate cd and then editing the menu.lst would do the trick but I don't have a clue. 

Thanks.

---

### Post by Sims2789 on 2007-11-20
> **bem202 said:**
> I am trying to install ubuntu on a toshiba portege 3480CT with no cdrom or floppy. It also will not boot to usb drive. It also has no ethernet port. BUT I do have the ability to rip the HD out of the sucker and put it in a usb HD caddy which I can then attach to my desktop.  I have tried installing the live and alternate cd's to it via the desktop BUT when I put it back into the toshiba it doesn't boot. 

It has 192mb of ram and a 20gig hard drive. I am considering Xubuntu but have run into the same problem there. 

Any ideas. I think installing to the HD via the alternate cd and then editing the menu.lst would do the trick but I don't have a clue. 

Thanks.

If you know someone with the [I exact[/I] same model (RAM, graphics card, possibly processor, etc. may be different, but the motherboard and BIOS must be the same) and they have a CD-ROM drive then you can install it on theirs and bring it over to yours.

---

### Post by zach12 on 2007-11-20
Put the hard drive in a pc and boot the xubuntu cd and install on the lappy hard drive.
Then put the hard drive back in the laptop (you will have to reconfig xserver) but it should work
just a idea

or if you have windows and i would use wubi 

Have fun:)

---

### Post by Sims2789 on 2007-11-20
> **zach12 said:**
> Put the hard drive in a pc and boot the xubuntu cd and install on the lappy hard drive.
Then put the hard drive back in the laptop (you will have to reconfig xserver) but it should work
just a idea

or if you have windows and i would use wubi 

Have fun:)

That won't work unless the BIOSes are identical, so he needs to use a computer of the same model but with a CD-ROM drive.

---

### Post by gupta_sumesh63 on 2007-11-20
RAM is only 192 MB. He needs a minimum of 256 I feel for installation. Go for a bit more of RAM. It should solve the problem I think.

---

### Post by meindian523 on 2007-11-20
I guess if he could install on a portable HDD using a lappy with a similar configuration,he could put it in a spare bay(master or slave) and clone it to his main HDD,it would be fine(obviously including the MBR too),won't that be possible??

---

### Post by bem202 on 2007-11-21
Thank You all for the quick responses. I am currently typing this post on the toshiba but it is running happy puppy linux (HPL). I will explain how I got it running hoping that it will shed some light on some ideas on how to get Xubuntu or Ubuntu running. 

From within the HPL live cd, running on my desktop pc, I installed it (HPL) to a partition that I had formatted to Fat32. I then used Syslinux, after booting back into windows, with the -f -ma command to force it to format the (mbr?) of the installed partition to make it bootable. It worked. 

What I am thinking now....

I install Xubuntu via the alternate cd to the Hd via the caddy and my desktop. BUT I keep the partition I install it to formatted to Fat32. I then use Syslinux with the -f -ma command attempt to boot to that partition. I then cross my fingers.

I will keep the post...posted.

---

### Post by bluepowder7 on 2007-11-21
here's a silly idea.  is it possible to copy the ISO image of the install CD onto the lappy hard drive, and then use some kind of utility to read the giant ISO file as if it were a CD-ROM disk?  that would be kind of like running the CD directly from the hard drive, which you would be able to do on the laptop itself.

---

### Post by bem202 on 2007-11-21
Thank You all for the quick responses. I am currently typing this post on the toshiba but it is running happy puppy linux (HPL). I will explain how I got it running hoping that it will shed some light on some ideas on how to get Xubuntu or Ubuntu running. 

I installed HPL onto the HD, using windows on my desktop and the HPL live cd. From within the HPL live cd, I installed it to a partition that I had formatted to Fat32. I then used Syslinux, after booting back into windows on the desktop, with the -f -ma command to force it to format the (mbr?) of the installed partition to make it bootable.

What I am thinking now....

I install Xubuntu via the alternate cd to the Hd via the caddy and my desktop. BUT I keep the partition I install it to formatted to Fat32. I then use Syslinux with the -f -ma command attempt to boot to that partition. I then cross my fingers.

I will keep the post...posted.

---

### Post by meindian523 on 2007-11-22
> **bluepowder7 said:**
> here's a silly idea.  is it possible to copy the ISO image of the install CD onto the lappy hard drive, and then use some kind of utility to read the giant ISO file as if it were a CD-ROM disk?  that would be kind of like running the CD directly from the hard drive, which you would be able to do on the laptop itself.

that's possible......there are utilities in Windows,and you can use the man page of the mount command to mount it as a device in Linux.....

---

### Post by meindian523 on 2007-11-22
I guess the OP can use this HOW-TO:

[http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)

Xubuntu is just Ubuntu with XFCE Desktop Environment....

---

