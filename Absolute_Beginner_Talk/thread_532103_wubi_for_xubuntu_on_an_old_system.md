---
title: "wubi for xubuntu on an old system?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2007-08-22
I have an old laptop IBM 240 thinkpad, which has 128mb of ram and has 5.5GB of disk space and 3GB of free diskspace.  The system already has win2k on it and I wanted to make it into a dual boot system.

The problem is that the bios is so old that the usb cdrom I have I don't think will boot from since the bios is so old and I can't figure a way to install Linux on it any other way except with wubi.

I wanted to put xubuntu, since xubuntu only requires 1.5GB of free HD space and 64MB of ram.  I've been happy with xubuntu on some older systems as well.  Then looking at wubi's website requirements it says:

What are the system requirements?

256 MB RAM and an 1 GHz or faster Intel/AMD processor is recommended for optimal performance, though Xubuntu might work on less. As for disk space, the installation requires a minimum of 4GB. This space is mostly used by the virtual hard disk file. Most computers purchased within the last 3 years should be able to run Ubuntu fine, and Xubuntu is suitable for older computers.

Is there anything I can do to get xubuntu on this system or any decent linux distro?

---

### Post by bluenova on 2007-08-22
I did an xubuntu wubi install on a simlar IBM model with 96mb ram. It runs ok even with a few firefox tabs open, but installing /updating software gives it problems, even using apt-get / aptitude.

---

### Post by Terl on 2007-08-22
Do you have a floppy drive as well?  I have an old IBM laptop tool.  It will not boot with the cdrom but I found a wonderful disk on a slackware cdrom called sbootmgr.  It boots from the floppy and then makes the computer boot from the cd....very nice little tool.

As for your specs, I have not tried Xubuntu on my old 766XD but I have used slackware without a problem; you just have to use a lightweight window manager.

Might be a long way around, but I would definitely get the sbootmgr and use it to boot the cd for xubuntu.  What have you got to lose :)  If that did not work, slackware is very nice, especially if you are willing to learn.

---

### Post by bone2006 on 2007-08-22
bluenova when running wubi just now it warns me that I need at least 4GB of free disk space, which I do not have, it stops right there in the tracks.

---

### Post by bone2006 on 2007-08-22
Terl  :
I have an old floppy, but the system only has one usb via floppy.  The bios lets me boot from floppy, but I'm not sure if I could boot from the floppy, then remove the usb and then plugin the cdrom?

---

### Post by bone2006 on 2007-08-22
sorry for posting so many questions.  I just found out that the floppy wasn't usb, it's another connection.  So now I have a usb cdrom and another connection has the floppy connected.  Can I download 
sbootmgr from [http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm) and have say xubuntu alternative cd and then install it that way?

---

### Post by CocheseUGA on 2007-08-22
Here's what I did for my Ubuntu install:

I took out the HDD and put it in an external case and used another computer to run the live CD.

Before I removed the drive from the other computer, I had to change a couple of files to make it show as hd0 versus hd2, which is what it showed with the other internal drives installed.

It can be done, unfortunately I don't remember which two files I edited. I'll try to remember.

---

### Post by Terl on 2007-08-22
Rats!  Mine has a cdrom and I have an external floppy.  There are distros that you can install with floppies.  They let you get the bare system on and then you can get the rest from the cd later.  

There are some ideas here:  [Installing Linux w/o cd, usb, floppy, etc.]("http://marc.herbert.free.fr/linux/win2linstall.html").  Maybe there are ideas there.

Do you have an internet connection for the computer?

EDIT:  Try this page if you have an internet connection.....[Installation/Netboot]("https://help.ubuntu.com/community/Installation/Netboot")

---

### Post by bone2006 on 2007-08-22
Yes I have a wifi 802.11g card, which is working in win2k and ethernet if I'm not mistaken, the laptop isn't infront of me right now.
I actually need internet and it's one of the main reasons why I want to put linux on it.  The only thing I really want is an updated version of firefox on linux.  It's for a person who really just wants to use the internet and browse as fast as possible and win2k on it is already slow.

---

### Post by Terl on 2007-08-22
I would look into that second link I posted.  It came from the ubuntu documentation library.  The net install seems to be the way to go.

---

### Post by bone2006 on 2007-08-22
I was looking at the instructions, but the http server and tftp server seems like it's kind of complicated.

The thinkpad has a sticker on it that says it's designed for Windows NT and Windows 98, yet there's windows 2K on it, so I believe this laptop must have had somebody install Win2k afterwards.  If so it seems that I should be able to boot from the floppy as it's an option in the bios and then hopefully the bootable floppy would tell my system to use the usb CD to install linux.   Or am I just waisting my time?

---

### Post by Terl on 2007-08-22
> **bone2006 said:**
> I was looking at the instructions, but the http server and tftp server seems like it's kind of complicated.

The thinkpad has a sticker on it that says it's designed for Windows NT and Windows 98, yet there's windows 2K on it, so I believe this laptop must have had somebody install Win2k afterwards.  If so it seems that I should be able to boot from the floppy as it's an option in the bios and then hopefully the bootable floppy would tell my system to use the usb CD to install linux.   Or am I just waisting my time?

No you should be able to do that.  I misread your other post I think.  I read it as "I can have a floppy or cd hooked up but not both".  I would try the floppy boot to make the cd boot.  The disk image is on the slackware cd's but you can probably find it right:  [http://linux.simple.be/tools/sbm]("http://linux.simple.be/tools/sbm")

I used that puppy to install all kinds of fun stuff on my laptop.  I especially liked FreeBSD :)

---

### Post by logos34 on 2007-08-22
> **bone2006 said:**
> I was looking at the instructions, but the http server and tftp server seems like it's kind of complicated.

The thinkpad has a sticker on it that says it's designed for Windows NT and Windows 98, yet there's windows 2K on it, so I believe this laptop must have had somebody install Win2k afterwards.  If so it seems that I should be able to boot from the floppy as it's an option in the bios and then hopefully the bootable floppy would tell my system to use the usb CD to install linux.   Or am I just waisting my time?

Afraid so.  AFAIK SBM (SmartBootManager) does not support USB boot (for now at least).  I just went through all this in another thread.  It's good only for internal devices. 

Netboot is the way to go.  The method you want to try is the net install from Windows:
[https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%2Ffromwindows%29](https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%2Ffromwindows%29)

If and when you get it going I'd install the smallest version possible, the server edition, considering how little room you have.  It's command-line only, but you can always install a gui by downloading the xubuntu-desktop package.

---

### Post by Terl on 2007-08-22
> **logos34 said:**
> Afraid so.  AFAIK SBM (SmartBootManager) does not support USB boot (for now at least).  I just went through all this in another thread.  It's good only for internal devices. 

Netboot is the way to go.  The method you want to try is the net install from Windows:
[https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%2Ffromwindows%29](https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%2Ffromwindows%29)

If and when you get it going I'd install the smallest version possible, the server edition, considering how little room you have.  It's command-line only, but you can always install a gui by downloading the xubuntu-desktop package.

Thank you, I did not know that about smart boot manager.  I am glad you saw this and helped out.

---

### Post by logos34 on 2007-08-22
On second thought, the 'CD approach' contained in the link I just gave you just might work in your case because it's following through the install from the cdrom rather booting from it.

---

### Post by bone2006 on 2007-08-22
The CD approach looks promising, but what if I screw up the bootloader or something, I'd have problems probably getting even windows up and running.
What I don't understand is that if a person was able to put in a windows bootable floppy and then have the CD in the CD rom, shouldn't I be able to do this with Linux as well?

---

### Post by logos34 on 2007-08-22
> **bone2006 said:**
> The CD approach looks promising, but what if I screw up the bootloader or something, I'd have problems probably getting even windows up and running.

Grub will overwrite your windows ntldr boot loader and ordinarily do so without a problem (it should add a windows boot entry to the menu), but if you don't want to take a chance you could download SuperGrub CD, which will allow you to boot windows or linux, as well as restore/repair the windows or grub boot loader.  

Or you could install Grub on a floppy (what I do with every new install until I'm sure everything works).  
The ubuntu alternate install gives you this option.  On the live cd there is also an option to change the default location (i.e. MBR of hd0):  when you get to the 'Ready to install' screen, click on the 'Advanced' button lower right and replace (hd0) with (fd0)--this sends it to a floppy. 

> What I don't understand is that if a person was able to put in a windows bootable floppy and then have the CD in the CD rom, shouldn't I be able to do this with Linux as well?

The issue here is that it's an **external USB** cdrom.

---

