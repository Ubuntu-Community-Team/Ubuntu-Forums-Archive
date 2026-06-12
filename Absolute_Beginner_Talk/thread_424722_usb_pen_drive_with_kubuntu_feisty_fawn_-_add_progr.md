---
title: "usb pen drive with kubuntu feisty fawn - add programs"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by mistergq on 2007-04-26
I have an old laptop where the HDD controller failed.  After I installed feisty fawn on my new laptop, I wondered "why wouldn't the live cd work with the old laptop so my wife can use it while watching tv?"  It did, and she thought it was great, but she wants java and flash.

So I discovered you can make a USB pen drive of the live cd.  I followed the instructions of the wiki to create a USB pen drive and that works for Kubuntu feisty fawn.  I then booted up and it worked (to my surprise).  I then installed firefox and changed the time.  rebooted so the time change is fixed, but when I rebooted, none of my changes were saved.  I guess those changes were made to the ramdisk and that was it.

My question is, how do I add programs.  Firefox is not installed with Kubuntu.  I also need to install flash and java.  Do I need to make my own live cd first, and then create usb key, or is there away I can add these programs to the usb thumb drive?  would it be possible to install Kubuntu directly to thumb drive?

---

### Post by lamalex on 2007-04-27
yeah you can install kubuntu to the thumb drive, there are about 1000 guides online. here is one of them . [http://lifehacker.com/software/ubuntu/how-to-install-ubuntu-linux-on-a-flash-drive-245087.php](http://lifehacker.com/software/ubuntu/how-to-install-ubuntu-linux-on-a-flash-drive-245087.php) and here is how to use the thumbdrive just to save your settings. [https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28drive%29%7C%28pen%29](https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28drive%29%7C%28pen%29)

---

### Post by ugbuntuoo on 2007-04-29
There are actually about 4000 guides online about installing ubunto TO a USB pen drive.   However, there are zero guides that address how to transform Feisty Fawn ISO files to a bootable USB key *for installation purposes*.  I don't want no stinkling LIVE pen drive.  I just need Ubuntu - the full Alternative i386 distro - to be installed on a bootable USB pen drive.  None of the previous guides that discuss Edgy or others seem to work.  I get errors like:

CP: cannot stat 'casper': No such file or directory   ... and so on.  I followed the instructions on Pendrivelinux.com verbatim... 8 times over the past 2 days.  Feisty Fawn (Ubuntu 7.04-alternative-i386.iso) installed like a charm onto my 1998 Sony Vaio laptop.  Now I just need to transfer the image to a pen drive to install it to a mini-ITX form factor device.

Can anyone help with references to create a reliable** installation **USB pen drive (not a Live pen drive) based on the latest version of Ubuntu?  I can run the install of a Windows XP PC, a Mandrake 10 desktop, or a Feisty Fawn 7.04 notebook .

Thanks in advance for considering us who don't care about Live USB drives, but rather need USB installation media!

---

### Post by Blippe on 2007-05-01
> **ugbuntuoo said:**
> There are actually about 4000 guides online about installing ubunto TO a USB pen drive.   However, there are zero guides that address how to transform Feisty Fawn ISO files to a bootable USB key *for installation purposes*.

There are actually tons of those too, most of them goes like this: 

0. make sure your computer and usbdrive support usbboot and turn on this in the bios.

1. download [http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current//images/netboot/boot.img.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current//images/netboot/boot.img.gz)

2. find out where your usbpendrive is mounted and extract the previous file directly onto one (preferably the first) partition on the drive: zcat boot.img.gz > /dev/sdXY 

3. Reboot with the usbdrive in the computer and install. 

(4. there might be a problem with grub, if so change '(hd1,0)' to '(hd0,0)', write this down. NOW!)

This will however demand a connection to the internet since we don't use any local repository (like a cd or an iso) check out this guide and change everything for fiesty if you want that: [http://ftp.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s03.html](http://ftp.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s03.html)

---

