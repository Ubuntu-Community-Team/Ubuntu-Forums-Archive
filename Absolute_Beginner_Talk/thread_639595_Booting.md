---
title: "Booting"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by salvatordarling on 2007-12-13
Hi everyone...

I've just started using Ubuntu (after months of persuading my wife that it's a good idea).  I currently have it installed on my external hard drive, because I didn't want to get rid of Windows until I was sure that all my hardware worked on Ubuntu.
I'm going to switch these operating systems over in the near future, but until then I have a little problem. 
Even though Windows is on my laptop's hard drive, I can't boot it without having the external drive plugged in.
A friend informs me that it is because the boot loader is on the external hard drive.  Is there any way that I can move this to the laptop's hard drive?  

Thanks

SalvatorDarling

---

### Post by dstew on 2007-12-13
It is important to understand the problem exactly. If the external drive is plugged in, do you get the grub menu when you boot the computer? If the external drive is not plugged in, what messages appear on the screen?

My guess is that the grub stage 1 is installed in the MBR of the hard disk. Stage 1 then gets the menu and its other code from the external disk. If the external disk is not plugged in, you might then get a grub stage 1 error, or perhaps nothing. The MBR part of grub is very small, only a few hundred bytes, and it cannot do very much by itself.

---

### Post by salvatordarling on 2007-12-13
The grub menu does appear when the drive is plugged in.  When it isn't, it gives the first grub message, then it says grub error.
I vaguely understand what you're saying, but I'm very new to Ubuntu and don't really have much knowledge of programming and computers in general underneath the operating system.
Is there a way of getting around this problem, so that it doesn't need the external drive to boot?

Thanks

---

### Post by dstew on 2007-12-13
From your answer, it is clear that grub is present in the MBR of the hard disk. If the external drive is not attached, the part in the MBR cannot load the rest of grub, so it fails.

If you want to have a dual-boot capability with an external drive there are several ways to do it. One way is to put a /boot partition on your hard disk. Then, grub will have all the parts it needs to boot Windows even when the external drive is not attached. Another way is to make the external drive bootable by altering the BIOS order. Often, though, the BIOS will be unable to boot from an external drive. I recall that USB 2.0 drives can sometimes be bootable, but it depends on your BIOS. You would have to change the BIOS boot order to look for the external drive first, then the hard drive. If you can make the external drive bootable, you would need to install grub on the external drive, and you could leave the hard drive as a pure Windows bootable drive. You can also make a bootable floppy with grub and its menu on it, if you have a floppy drive in your notebook. There are probably other ways to work the problem, these are the ones that I can think of at present.

---

### Post by salvatordarling on 2007-12-13
Thanks, I'll give these a try.  I think that I might just partition my hard drive and install Ubuntu on the second partition, and only use the external drive for files.  
Thanks for your help!

---

### Post by erfahren on 2007-12-13
In case you haven't come across it, there's some excellent information on GRUB and the MBR at this site. He also talks about WinGRUB, which may be an option for you. (I'm not sure if that would work with Vista) you'd have to restore your current MBR before using that in any event).

Anyway, take a look at what he says about GRUB, WinGRUB, the MBR, and the other options.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Duck2006 on 2007-12-13
> (I'm not sure if that would work with Vista)

No it does not you would have to use some think like EasyBCD for that to work.

---

