---
title: "Problems with boot up"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Jimmy9pints on 2008-03-31
I previously installed Ubuntu to try it out and I really liked it. However, I experienced boot problems that ultimately lead to me (against my will) going back to windows.

I have been keen to get rid of Windows for a long time - ultimately I would like to use opensource in all my home and business operations...but first I have to learn it myself, hence my keeness to try again.

Anyway, on to my question:

Last time I tried to have a dual boot system, Ubuntu and Xp. The problem was, that after I installed Ubuntu and tried to reboot I got a NTLDR missing error. Then, by chance, I tried to reboot with the XP CD in the drive - it loaded grub and I had the choice of the two operating systems and I could happily boot either OS. If I ever took the CD out, it would not load grub and I could not boot either OS. I thought it very odd.

Then, I tried using the windows CD to load the recovery console and entered a FIXBOOT command. Upon rebooting it logged straight into Windows and Ubuntu was never to be seen again...

Anyway, here I am again trying to use Ubuntu. Because apart from this glitch I was happy with Ubuntu, I totally got rid of windows and installed a single boot system. However, I still have the same problem. It will not boot up unless the windows CD is present - sorry I can't remember the error message it gives me this time. But in anycase, the Windows CD loads grub and it automatically loads Ubuntu.

---

### Post by forestpixie on 2008-03-31
Try to reinstall grub - you can do it with the buntu livecd or get a copy of supergrub

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

That was likely all you needed to do last time as well :)

---

### Post by Jimmy9pints on 2008-03-31
Thank you for your reply! 

I will try that.

---

### Post by bumanie on 2008-03-31
I would try the fixboot; fixmbr fix for xp again and then reinstall grub. Before doing that, could you copy and paste the output of sudo fdsik -l (that's a lower case L). I do know that I had similar trouble on an older computer and despite the /boot/grub/menu.lst being correct, the computer would never boot correctly. I actually resorted to booting with super grub disc (SGD) when I needed windows and I set up grub to boot straight into ubuntu. Not sure, but I suspect it was the bios instructions that were mucking things up, but as it was an older computer, I already had the 'latest' bios firmware. Of minor interest I have a friend who has a similar problem and boots ubuntu with SGD - he leaves his kids on windoze and uses ubuntu exclusively himself. My previous computers architecture was circa 2003, as is my friends. Might be an idiosyncratic problem with some bios firmware. On my new computer any edits to grub or fstab work fine.

---

### Post by dstew on 2008-03-31
> I tried to reboot with the XP CD in the drive - it loaded grub and I had the choice of the two operating systems and I could happily boot either OSThis shows that your problem originally was that the BIOS enumeration of the hard disk partitions changed when the CD was removed or replaced. That is, when you originally installed (with a CD in place) your CD may have been counted as (hd0), and your hard disk partitions (hd1) and (hd2). When grub was installed, it was embedded with a block address to look for Windows on (hd1) and Ubuntu on (hd2). But, when you removed the CD, your hard disk partitions became (hd0) and (hd1). Now, grub is still looking for Windows on (hd1), which is really an Ubuntu partition, and it is looking for Ubuntu on (hd2), which isn't there, hence the errors.

It could have been fixed by reconfiguring grub, or re-installing it.

---

### Post by Jimmy9pints on 2008-04-03
I guess it's normal as a newbie to feel totally out of your depth all the time!

Anyway, *TRYING* to follow people's advice, I opened a Terminal, typed sudo grub and got the grub prompt. 

Then I typed "find /boot/grub/stage1". and (hd1,0) was the response. So then I typed root (hd1,0) and then setup (hd1,0). 

Upon restarting, I got:

Grub Loading stage1.5

Grub loading, please wait...
Error 17 cannot mount selected partition 

I there are plenty of posts about this, so I will try doing what they say.

Thanks.

---

### Post by dstew on 2008-04-03
> Then I typed "find /boot/grub/stage1". and (hd1,0) was the response. So then I typed root (hd1,0) and then setup (hd1,0).
Did you do this from your hard-disk Ubuntu system or from a Live CD boot? Do you have more than one hard disk in the system?> Grub loading, please wait...
Error 17 cannot mount selected partition Did you get this error after selecting a menu item, or before the menu appeared?

Also, please post the output of```
sudo fdisk -l
```

---

### Post by Jimmy9pints on 2008-04-05
Hi, and sorry for the late reply. 

> Did you do this from your hard-disk Ubuntu system or from a Live CD boot? Do you have more than one hard disk in the system?

I did this from my hard disk installed Ubuntu. Yes I have two hard disks, one SATA 320GB one regular HDE 120GB.

> Did you get this error after selecting a menu item, or before the menu appeared?

Before selecting a menu item. After receiving this error, I have the option of going into the menu but it doesn't matter which option I select, none of them will load. 


And the output from sudo fdisk -l is:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7e0a7e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38538   309556453+  83  Linux
/dev/sda2           38539       38913     3012187+   5  Extended
/dev/sda5           38539       38913     3012156   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0aec6b00

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14593   117218241    7  HPFS/NTFS


The SATA 320GB is the disk that holds the system and the HDE 120GB holds all my music. This leads me on to another question, how do I permanently mount the 120GB so I can access my music all the time in Ubuntu. 

Thanks, Jimmy.

---

### Post by dstew on 2008-04-06
> I did this from my hard disk installed UbuntuFrom the rest of your post, it seems you can only get into the hard disk Ubuntu if something is in the CD-ROM drive, right? So, was your grub **find** command executed when a CD-ROM drive was in the drive, or not in the drive? Did you take the CD out after you got into Ubuntu?

It probably does not matter, because if you *boot* with a CD in the drive, the BIOS enumeration will be different than it is if you boot with no CD in the drive. So, even though your /boot/grub/stage1 file is on sda1, which *should* be (hd0,0), when the CD is in there, sda1 is enumerated by the BIOS as (hd1,0).

You installed grub to find its root directory in (hd1,0). Then you take the CD out. Then you reboot, but now, grub's root directory is in (hd0,0), and grub can't find it.

The only sure way out of this problem is to make a [grub boot floppy]("https://help.ubuntu.com/community/GrubHowto/BootFloppy"), and use it to install grub when there is no CD in the drive. Then the BIOS enumeration will be correct.

---

