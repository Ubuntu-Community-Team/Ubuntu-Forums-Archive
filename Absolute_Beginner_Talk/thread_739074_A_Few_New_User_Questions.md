---
title: "A Few New User Questions"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by tombarchoc on 2008-03-29
I am new to Linux, trying to find an alternative to Vista which has been nothing but trouble for me. The Vista laptop will remain due to apps I use every day that do not run under Linux. But I've decided to try and dual boot XP and Ubuntu on my home desktop.

I've used the live CD and have been generally happy but not being able to save changes is very annoying and its slow running off of the CD. I can't really try it out as a real everyday alternative. My browser has bookmarked an article detailing what I need to do to set up dual booting. But I have a few silly beginner questions for those of you who have done this already:

1. How often does the dual boot option fail during installation? If it does fail, is there an easy way to get the computer back to just XP mode? Is there anything I have to watch out for?

2. I intend to load Ubuntu on a USB-removable hard drive. This drive will not be used anywhere else, just on this computer. Will that cause any problems? My very old Pentium-4 desktop does not boot from USB.

3. If I install 7.10, will the dual boot still work if I decide to upgrade to the new version 8 that is coming? Does it just upgrade or do I have to reinstall the OS?

Here is the biggest question, honest answers please! I use the computer to get work done, not to play with computers! Is there another distribution other than Ubuntu that would be better suited for someone like me?

Thank you for any information you can give me.

barchoc

---

### Post by Dr Small on 2008-03-29
So where is XP located? Is it on an internal drive, or on the USB removable hard drive?

I have only had GRUB fail to install 1 out of 10 times, so it is pretty rare.
If you install Ubuntu on the USB drive, your BIOS must be able to boot frow USB device and it must be first priority.

Now to the questions:
1.) GRUB does not fail very often.
2.) This all depends upon where XP is located.
3.) You will be able to upgrade to the newest version, and generally works most of the time, but there have been people that it broke the system on.

My general rule is, if it work, why upgrade? :D

Dr Small

---

### Post by Moop on 2008-03-29
Hi, 

The dual boot install is simple and shouldn't cause any problems. If something does go wrong it's easy to restore to booting XP as long as you have a bootable XP cd. 

I've never installed to a USB drive so can't help you with that. 

You can install 7.10 and then upgrade without it affecting your dual boot setup. I'd suggest installing 8.04 beta now. It's going to be released soon anyway. 

I think Ubuntu is a good choice. It doesn't take much configuration to get it working the way you want. You could take a look at Linux Mint which has a few more things that just work "out of the box".

---

### Post by Mauler5858 on 2008-03-29
One MAJOR issue is that with a basic install onto a USB hard drive is that:

Linux writes over your MBR with a pointer to grub which will be on the USB drive.  If the MBR doesnt see the USB drive(unplugged) booting will fail.

This, however, will not be a problem if the USB hard drive is always attached to your machine on startup. (obviously if your booting linux it will be, but it has to to boot your xp)

---

### Post by tango_ninja on 2008-03-29
hi! welcome to the forum :)

hopefully we can help sort this out for your so you can experience and enjoy ubuntu.

1. grub does not fail that often, but i have heard of it before (never failed on my system)

2. if you're installing Ubuntu on a USB HD, why not simply configure your computer's boot options to boot primarily from USB HD and then from internal HD (assuming your XP is internal). then you can just plug in the USB HD for ubuntu and leave it unplugged when wanting to boot XP [EDIT] oh nm i  see your computer does not boot USB HD

as for the other 2 questions, i'm not really that sure.....

---

### Post by Dr Small on 2008-03-29
> **Mauler5858 said:**
> One MAJOR issue is that with a basic install onto a USB hard drive is that:

Linux writes over your MBR with a pointer to grub which will be on the USB drive.  If the MBR doesnt see the USB drive(unplugged) booting will fail.

This, however, will not be a problem if the USB hard drive is always attached to your machine on startup. (obviously if your booting linux it will be, but it has to to boot your xp)
My question is,
If Ubuntu is installed to the USB drive while the internal drive is unplugged, the Windows MBR is not overwritten, correct?

So when Boot Priority is on USB, and the USB is plugged in, it loads GRUB and boots ubuntu. When the USB drive is unplugged, it boots the hard drive and loads Windows MBR, correct?

Dr Small

---

### Post by Mauler5858 on 2008-03-29
His computer will not boot USB Dr_Small

---

### Post by Dr Small on 2008-03-29
> **Mauler5858 said:**
> His computer will not boot USB Dr_Small
Ah, ok. I see now. Thanks for pointing that out. That complicates matters.
Well then, GRUB would need to be installed on the internal drive and have an entry to point to the USB drive, would it not?

---

### Post by chewearn on 2008-03-29
My advice for a new user wanting to try out ubuntu (or linux in general); avoid installing to usb drive if you can.  Occasionally, I still see grub error posts of people with usb install.  This is just my advice.

I think there are less problems with simply dual boot on the harddisk.  For the real paranoid, you can physically swap harddisks (I did long time ago, when I first started on the path down linuxland).

But, thanks to the hardwork of ubuntu developers, you can try Wubi option with the new Hardy 8.04.  Simply pop-in the livecd while you have Windows running.  The autorun will execute the ubuntu installer.  With this method, ubuntu will install into a folder under Windows.  If you got tried of ubuntu, simple run Windows and uninstall Wubi from Add/Remove Programs.

---

### Post by Mauler5858 on 2008-03-29
My advice..Try It.  If you try it out and notice boot errors and cannot get back into windows xp do not panic.  Boot to your XP install disk and at the menu go to the recovery console.  Type fixmbr into the command line and you will be back to flawless single boot.

---

