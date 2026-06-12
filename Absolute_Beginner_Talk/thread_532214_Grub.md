---
title: "Grub"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by moshii on 2007-08-22
Hi,

I've got a weird problem with GRUB. At the start, I couldn't manage to get it to find my Vista installation, so I made Vista's Boot Loader Default-before I realised that you can't just edit the boot.ini like XP. So that didn't work, I managed to boot back into Ubuntu using the CD, and selected "Boot from the First Hard Drive". I then fiddled with the setting in GRUB a second time, and managed to locate my vista installation for GRUB Successfully.

However, I had to now had to set GRUB as the default boot loader again-which went fine according to Ubuntu BUT whenever I go to select any of the options, Vista or Ubuntu I get an error message- can't remember it exactly, but it is something to do with "invalid partition" or "no install found on this partition" HOWEVER, when I put in the Ubuntu CD and go "Boot from the First Hard Drive" ALL of the options work...?

Anyone with any ideas?

---

### Post by Dave54 on 2007-08-22
are ubuntu and vista on the same hard drive or different ones? If they are on different hard drives try changing your bios settings to boot the other drive, or fiddle around with other options.

(I suggest this because a similar situation happened to me)

---

### Post by jamvegan on 2007-08-22
If Dave54's bios suggestion doesn't fix your problem, you might take a look at the following.

In the file /boot/grub/menu.lst, each bootable option has a line like:
```
root            (hd0,1)
```
and the Ubuntu entry also has a line like:
```
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=b497a47a-fd39-41e1-8774-ab4dd239d2f1 ro quiet splash
```

Both of the examples above are from my actual /boot/grub/menu.lst entry for Ubuntu.  They refer to the second partition on my first hard drive.  This can also be referred to as /dev/hda2.

The first thing that I would check is whether or not the entries in your /boot/grub/menu.lst file refer to the correct partitions on the correct drives.

Note that the following portion of my kernel line:
```
root=UUID=b497a47a-fd39-41e1-8774-ab4dd239d2f1
```
could be replaced with:
```
root=/dev/hda2
```
and that is what I would do if I thought it might be causing me problems, since I have no idea how to determine what the correct hex string would be.

---

### Post by Bethrine on 2007-08-22
I'm new to linux and have Vista and just had this problem, see this thread...

[http://ubuntuforums.org/showthread.php?t=531451](http://ubuntuforums.org/showthread.php?t=531451)

I can dual boot, but my Vista is messy (loads to a blank screen)

p.s. start with post #7, i'm a definate new person!

---

### Post by moshii on 2007-08-22
Hi. Sorry, both my operating systems are on the same Sata Hard Drive- (hd3) according to ubuntu. 

Ubuntu is (h3,1) and Vista is (hd3,0). I will try what you have suggested in a little while jamvegan, however I still find it strange that the cd seems to read the menu.lst ok, yet the grub install on my hard drive doesn't-can you reinstall GRUB?

---

### Post by annda on 2007-08-22
Hi,

just a quick comment: hd3 is h2 for GRUB - you should correct this.

some more info about configuring GRUB:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by jamvegan on 2007-08-22
> **moshii said:**
> can you reinstall GRUB?

Yes, see this Ubuntu community documentation: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

