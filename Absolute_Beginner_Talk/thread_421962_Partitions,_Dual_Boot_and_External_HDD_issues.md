---
title: "Partitions, Dual Boot and External HDD issues"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by trishacupra on 2007-04-24
I've just installed Feisty on my laptop with external hard drive, which dual boots with Windows XP.

My plan was to install Feisty on my laptop's internal hard drive alongside WinXP, but even after several defrags, it seems Windows scattered unmovable files all over my hard drive. And even though I ran chkdsk to fix all errors (and it did and then said it was clean), when installing Ubuntu it  refused to use my internal hard drive due to it having some kind of disk error. 

The options were all new to me, and I ended up with everything installed onto my external hard drive instead.

So, all my Windows stuff is on the internal hard drive, and all the Ubuntu stuff is on my external hard drive.

I wouldn't mind that, except I need to turn on the external hard drive when I turn on my laptop, or I get a Grub error (21 - which I believe is 'hard drive not found', which makes a lot of sense).

What I'd absolutely love is to set things up so that if I don't have my external hard drive turned on, then Windows would automatically boot up. If I do have the external hard drive turned on, I'd love Ubuntu to automatically start up.

I've read all I can find about dual booting on two hard drives. I want to run my plans past the forum for feedback on whether what *I think* will work actually *will*.

Theoretically, this is what I think I should try. There are big gaps in my knowledge, so if there is a better way (probably is) then please let me know.

First, I'm going to try to restore my Windows MBR. I have a laptop with the stupid recovery disk stuff rather than a Windows CD. So, I'm going to try using the Super Grub Disk at [http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home) to restore that. If that doesn't work, I'll try using a 'borrowed' WinXP disk to fix the MBR.

I think I may need to put Grub on the external hard drive, to make it able to boot up if I change the boot order to boot from my external hard drive first (if that's even possible - I'm just guessing I can). If my external HDD isn't connected, I'm hoping the boot order will then boot from the internal hard drive. The boot order would be CD, then external, then internal.

I'm hoping I can keep my installation of Ubuntu and not have to install it again. But I will if I must. And I'll try to figure out how to install Grub on the external hard drive, either using the Super Grub disk if possible, or when reinstalling. (To reinstall, do I just delete the Ubuntu partitions using gparted on the live CD then install again?)

Then I want to use gparted to create a separate home partition, but that's another issue...

Am I on the right track, or not?

Thanks.

---

### Post by Happy_Man on 2007-04-24
I would think it would be easier to change the order of OS's in the GRUB list so that XP is set to boot first. If you want to boot Ubuntu, it would give you ten seconds to turn on your external hard drive and boot Ubuntu before it auto-boots XP. To do this, edit /boot/grub/menu.lst and scroll down and switch the boot order.

---

### Post by trishacupra on 2007-04-24
Would changing the GRUB list stop the Error 21? Right now, that's all I get with the external drive turned off - no menu options at all.

---

### Post by Happy_Man on 2007-04-24
Oh, I see; you have GRUB installed to your external drive? If so, you will have to reinstall on your internal hard drive, otherwise what I suggested won't do anything.

---

### Post by trishacupra on 2007-04-24
This is from my GRUB menu list. How should I edit it?

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a60e46bc-de9c-4023-88e1-c984c569dc5b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a60e46bc-de9c-4023-88e1-c984c569dc5b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by trishacupra on 2007-04-24
How can I tell where I have GRUB installed?

---

### Post by Happy_Man on 2007-04-24
Try this:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title Windows NT/2000/XP
root (hd0,1)
savedefault
makeactive
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

title Ubuntu, kernel 2.6.20-15-generic
root (hd1,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=a60e46bc-de9c-4023-88e1-c984c569dc5b ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd1,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=a60e46bc-de9c-4023-88e1-c984c569dc5b ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd1,1)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


If somebody could please make sure this right, that would be nice. Just so that I know I haven't messed it up or anything. Trish, remember to back up your original menu.lst before you edit it.

---

### Post by trishacupra on 2007-04-24
Okay. I haven't tried changing the GRUB menu yet. Here's what I've discovered with some experimenting:

1. Yes, I CAN change the boot order to make my external drive boot before the internal one. Cool.

2. At the moment, if I boot the external drive first, it gives me an error about not being able to find the operating system or something. So, I'm guessing I have to install GRUB on this drive?

3. Looking at the Super Grub disk, it gives me the ability to restore the MBR for Windows. Cool, considering I have no install disk for Windows.

4. I'm not sure I can use the Super Grub disk to set up my external hard drive to boot Ubuntu automatically when I have the external hard drive set up to boot first in my BIOS. 

Here's a question - what makes Ubuntu load up when it's not a dual boot scenario? Do you still need GRUB to load up Ubuntu if you're not dual booting? Just wondering why changing the boot order isn't making Ubuntu load up at the moment. 

Where on earth is my GRUB installed? Is it on my external drive, yet there's something in the MBR on my internal drive that looks for it, which is why I get the error with the external drive turned off? How can I tell?

---

### Post by trishacupra on 2007-04-24
Okay, I think I'm getting somewhere. I just used the Super GRUB disk to restore the Windows MBR, which looks like it worked, but I'll reboot again (I'm in WinXP now) just to check. I also used the disk to install GRUB on the external hard drive - I think. I have to change the boot order and see. Fingers crossed.

---

### Post by Happy_Man on 2007-04-24
Well, see, normally I would say that GRUB has overwritten the MBR of Windows, which is why Super GRUB provides the option to restore it. But, as your install has been put on an external drive, it makes things a bit harder to figure out. But, as you say you can configure your BIOS to boot external  before internal, all you would have to do is install GRUB to that drive, and that should do it.

---

### Post by Happy_Man on 2007-04-24
WAIT!!! While you're in Windows, install the ext3 windows driver from [http://fs-driver.org](http://fs-driver.org). It'll make stuff that much easier...

---

### Post by trishacupra on 2007-04-24
Already done that. :) 

But thanks anyway.

---

### Post by trishacupra on 2007-04-25
All done. I got everything set up how I wanted it. I fixed the MBR so Windows boots up if the external drive is off. The BIOS is set up to boot from CD, then external, then internal. And I installed GRUB on the external drive, so Ubuntu automatically boots up when the external drive is on.

If anyone wants details, just ask.

---

