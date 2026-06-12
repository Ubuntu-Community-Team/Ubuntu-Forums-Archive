---
title: "Install Grub to External USB Floppy Drive"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by jmaldon on 2008-01-12
Hi,

I asked this in installation and upgrades and general help forums but no reply. maybe someone can help here?

Can someone please explain how to install grub to an external usb floppy drive rather than to the hard disk when installing a fresh copy of ubuntu?

I'm using the alternate install cd and when it asks where to install grub to (mbr) i choose no then try to specify /dev/fd0 or (fd0) and it gives me a fatal error.

i've had success when installing pclinuxos (specifying /dev/sdf?!?!!?!?!?!?!?!?!) but when i try the above and /dev/sdf i still get these fatal errors.

what am i doing wrong please? i'm getting a new dell laptop soon and don't want to overwrite the dell mbr just yet so was thinking of installing grub to floppy.

does it make a difference that it is an extrnal usb floppy and therefore i dont refer to it as fd0?

many thanks.

---

### Post by wjp.reg on 2008-01-12
[This helped]("http://www.pendrivelinux.com/") for me 

Good Luck!

---

### Post by bill516 on 2008-01-12
An excellent link.  Pendrivelinux.com would be the place to go, I think.

But you might try this little gimmick with your new Dell.  I do this on an ASUS laptop that has Kubuntu 7.10 installed on a 4 gig pendrive with no mbr alteration on the HD.

I'll assume you have installed a Linux op system on the pendrive without installing GRUB.

Next see if you can reset the Dell bios so that it recognizes the USB as a potential boot device.  It may refer to the USB stick  simply as a "removeable device."  Set your boot order so that removeable device is first. (strictly speaking not necessary I suspect, but that is how I have it.)

Now put the USB stick in the machine and reboot.  As you reboot press F1 (or perhaps F8) and see if the Dell bios gives you a list of "bootable devices" in a window as my ASUS does.

At that point just highlight the pendrive, press "Enter" and off you go in Linux.

One limitation.  Not all bios's allow this so if you want to carry the usb pendrive around and start it on pretty much any machine you will do better with the install instructions at pendrivelinux.com.

However you do it I encourage you to try booting your USB drive.  It really is very nice alternative.

---

### Post by dstew on 2008-01-12
You will first have to know the device name of your external floppy drive. Usually it will be something like /dev/sdb. I doubt it would be /dev/sdf, and it will certainly not be /dev/fd0. Can you boot your Ubuntu system with the BIOS or with a CD? If so, you can figure out the external floppy device name using the **fdisk **command. If you create a [SuperGrub CD,]("http://supergrub.forjamari.linex.org/") you can boot your hard disk Ubuntu installation from that.

---

### Post by Sef on 2008-01-13
Locked. [Duplicate Thread]("http://ubuntuforums.org/showthread.php?t=664950").

---

