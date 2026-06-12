---
title: "Dual Boot w/ Windows XP, Comp has 4 HDD's"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by LordKelvan on 2007-06-02
Hi:

I am a bit of a n00b, so bear with me (and try to give me the option that is most idiot-proof).  I want to dual-boot with Windows XP and Ubuntu, but I have 4 hard drives.  I have read some guides, but they all seem to implicitly assume that I only have 1 hard drive.  I guess I am wondering what is the best option for me?  Should I follow the usual suggestion of using the LiveCD to do a guided partition of the hard drive containing my Windows XP installation?  If so, do I have to first defrag my Windows drive?

A little background:  

1) I will be using Ubuntu to do some kernel-hacking for my graduate work (so it will, in the foreseeable future, be used for educational purposes only).  Specifically I will be running VMWare on Ubuntu, and kernel-hacking Ubuntu installations running on virtual machines (this is so that I can make mistakes when hacking without hosing the machine).  As such, I probably won't need to share any files between the Windows and Ubuntu installations.

2) My computer has 4 hard drives: 3 SATA (one of which has my Windows XP installation+Apps), and 1 IDE.  I  believe the SATA ones have NTFS and the IDE one has FAT32.

Thanks in advance.

---

### Post by la3875 on 2007-06-02
Well, in my limited experience it sounds like you might want to consider dual booting on separate drives to preserve your windows install, or that you might want to run Ubuntu virtually in Vmware on top of XP. Regardless an invaluable resource relative to the dual boot scenario can be found here: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/).

Best of luck.

---

### Post by richempire on 2007-06-02
You could try the live CD deal, but any changes made, you won't be able to preserve. As the fellow before, since you're going to be messing with the kernel quite often, I'd run it on a Virtual Machine inside of XP unless you REALLY have to install it on native hardware, that way even if you render Kubuntu unusable, you can still do homework under XP.
Another option is to pull out one of the hard drives, connecting it via USB and plugging it only when you're booting in Linux.

---

### Post by freebird54 on 2007-06-02
A further option - depending on your system BIOS, is to swap the 'boot drive' option in the BIOS when changing OS.  This leaves the drives separate, and does not even require a bootloader change on the XP drive.  For this scenario it coud be the best choice.

I would NOT run Ubuntu on the same drive, but you could also have it install to a different  drive, and put grub (the bootloader) on teh XP drive without otherwise affecting it... but then you would have to replace the bootloader if you ever removed Ubuntu (not that it's difficult but I'm lazy).  I think you have all the choices covered now - so enjoy!

---

### Post by regomodo on 2007-06-02
Just for experimentation i would try dual booting on different hard drives just so that if you mess up you don't mess the MBR of the XP partition. I did this to start off with but Grub wouldn't configure correctly. I now have XP and Ubuntu on the same HDD as it's the only way Grub will dual boot

It may have been just my MOBO but if you are just experimenting it's a good option

---

### Post by LordKelvan on 2007-06-02
Hi, thanks for the replies:

la3875 & richempire:  Here is the setup - I will be installing Ubuntu on one partition, then running VMWare on it, so that I can run Ubuntu on top of Ubuntu.  So essentially, I will have a permanent Ubuntu from which to run VMware, and then my kernel-hacking will be done on Ubuntu installations running on top of VMware (so that any mistakes I make will not hose the machine).  The reason for the convolution is that I only have Linux licenses for VMware.  I know that VMware offers some free stuff, but I will assume that there is something in the paid stuff that I will need or my prof wouldn't have requested it.  At any rate, I have to go with the above setup (otherwise your suggestion of running Ubuntu on top of XP would work).

So what I seem to be hearing is that installing it on the same drive as XP is a bad idea.  Could you guys provide some explanations as to why?  Does it have something to do with the fact that I have more than one drive?

freebird:  You mentioned that I could install Ubuntu to a different drive, but keep Grub on the XP drive.  Does this automatically happen when I tell the LiveCD to install to a different drive, or is there something else I must do?  As well, what do you mean I would have to replace the bootloader when I uninstall Ubuntu and how might I do it?  Is this true no matter which method of installation I choose, or just with installing Ubuntu to a different drive than XP?

---

### Post by freebird54 on 2007-06-02
If you keep the same boot drive, regardless of what OS you are going to run, then Grub will have to be in the MBR (Master Boot Record) to enable the choice.  The drive that Ubuntu is on makes no difference to this requirement.  If you at some future time want to remove the alternative OS, then you need to set the MBR back to Windows' expectations.  This is easily done with ***fixmbr***, or ***fdisk /mbr*** - which will overwrite the boot loader with the Windows 'equivalent'.

The reason for keeping it on a separate is just convenience, and the simplicity of not messing with your Win installation.  They both could be on the same drive without difficulty if you prefer that.

When you install Ubuntu, you can choose on which drive to put it - what partition sizes, types and numbers you prefer,  and where the Grub boot loader will go.  The default for the grub boot is to go on (hd0) - which is the current setting of boot drive.  This is the simplest setup in most cases, since you won't need to change boot drive settings at all.

There are as many possibilites as you have drives and patience for - but the two I have described are the simplest to get going (single boot drive, separate drives - and swapping boot drives) for most uses.  We can help you get anything going you decide on though! As you will note from my sig, I currently run a quad boot - and it was NOT difficult to make happen.

Enjoy!

---

### Post by bodhi.zazen on 2007-06-02
LOL

chroot anyone :

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

You can build your kernel in chroot if you like :)

---

### Post by LordKelvan on 2007-06-07
Thanks for all your suggestions - in the end I went with both OS's on a single SATA drive.  Of course, things did not go smoothly (my Windows installation was a bit messy, not Ubuntu's fault), but that is my problem :)

---

