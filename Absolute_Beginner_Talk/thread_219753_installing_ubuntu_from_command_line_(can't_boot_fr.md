---
title: "installing ubuntu from command line (can't boot from cd)"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by stephenk on 2006-07-20
Hi there,

my old computer can't boot from cds, so I need to use a Windows 98 boot disk to load the cd drivers before installing Windows.  How do I install Ubuntu from the command line?

---

### Post by Klemik on 2006-07-20
Hmm I think this document should help you:
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml)

Im not shure but it should be similar, anyway why cant you boot from cd ? Try to update your bios, choose boot device to cdrom.

---

### Post by stephenk on 2006-07-20
unfortunately, the computer can't boot from cds even with a bios update.  There's no way to select the boot device, so I'm stuck at a command line.  

I tried the website provided before but can't see how to install ubuntu using those methods - any other suggestions?

---

### Post by FlashDragon on 2007-01-25
I'm in a similar situation. I've got TWO machines that will require the use of command line Ubuntu installation. 

One is an old laptop that doesn't have enough RAM to support the Live CD. I can boot from the CD but it takes over an hour (and still waiting as I write) to bring up the GUI. Is there a way to just run the installation routine when the machine boots (I do get the Ubuntu options menu) or do I have to wait for the whole Live CD process to finish?

The other situation is a desktop machine that won't boot from a CD, period. I've done everything I could in the BIOS but it's just not happening.  We'll deal with that one later.

Thanks,

Pete

---

### Post by confused57 on 2007-01-25
> **FlashDragon said:**
> I'm in a similar situation. I've got TWO machines that will require the use of command line Ubuntu installation. 

One is an old laptop that doesn't have enough RAM to support the Live CD. I can boot from the CD but it takes over an hour (and still waiting as I write) to bring up the GUI. Is there a way to just run the installation routine when the machine boots (I do get the Ubuntu options menu) or do I have to wait for the whole Live CD process to finish?

The other situation is a desktop machine that won't boot from a CD, period. I've done everything I could in the BIOS but it's just not happening.  We'll deal with that one later.

Thanks,

Pete
I just gave a couple of links in this thread that may help:
[http://www.ubuntuforums.org/showthread.php?t=345923&page=2](http://www.ubuntuforums.org/showthread.php?t=345923&page=2)

If you have a floppy drive, you might want to look into Smart Boot Manager to boot to your cd drive:
[http://www.ubuntuforums.org/showthread.php?t=246486](http://www.ubuntuforums.org/showthread.php?t=246486)

---

### Post by anaconda on 2007-01-25
have you got a floppy drive.. it is possible to make a boot floppy, which will boot the CD.  

I have done this, but can't remember how...

---

### Post by FlashDragon on 2007-01-26
> **confused57 said:**
> I just gave a couple of links in this thread that may help:
[http://www.ubuntuforums.org/showthread.php?t=345923&page=2](http://www.ubuntuforums.org/showthread.php?t=345923&page=2)

If you have a floppy drive, you might want to look into Smart Boot Manager to boot to your cd drive:
[http://www.ubuntuforums.org/showthread.php?t=246486](http://www.ubuntuforums.org/showthread.php?t=246486)
Thanks for the advice. I've tried a couple of tactics from the links you gave me...still haven't nailed it down (yet) but I think I'm getting closer. Time ( a LOT of it) will tell....

---

### Post by M_the_C on 2007-01-26
I'm not sure if this would work, but though I should contribute.

My dad has a very old laptop that can't boot CDs.  It can boot Floppies but you can only have one drive in at a time.  (i.e. CD or Floppy)

Would you not be able to install GRUB onto the hard disk using a floppy, then configuring it to boot CDs (I'm pretty sure it can but have not checked).

---

### Post by IanW on 2007-01-26
Might it be possible for you to use a linux boot floppy like Tomsrtbt ([http://www.toms.net/rb/]("http://www.toms.net/rb/")) which should get you to a console with both CD and ethernet drivers, and do a CD or net install from there?

---

