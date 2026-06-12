---
title: "Dual Boot Problems, XP/Ubuntu 6.10"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by cbow12 on 2007-01-24
Install went fine.  I dedicated the IDE Primary drive to Linux and let Ubuntu format it.  My main drive is a SATA WD Raptor drive.  I had to install a PCI adapter card because my mobo didn't have an SATA port.
After Linux installation, I rebooted without the CD inserted and the system boots directly into Windows.  I tried F8 then F6 and dialog only shows the XP operating system.
I can boot into Linux with the CD inserted.
Any ideas would be appreciated.

---

### Post by mandrakethepenguin on 2007-01-24
You need to change the Primary and Secondary devices in your BIOS.  This is usually changed by pressing the F1 button repeatedly during startup immediately when your computer turns on and it should be in the BIOS main menu.

---

### Post by cbow12 on 2007-01-25
In my bios under BOOT there is an entry for Hard Disk Drives.  Entering this category, I find my two drives listed, the Win drive and the Linux drive.  The sidebar instructions say select the drive to be the boot drive.  I selected the Linux drive, pressed F10 to save and exit.  The computer still boots into Windows.
Another category under the BOOT menu is Boot Device Priority.  Under this category is listed First the Floppy drive, Second the Windows drive, and Third the DVD Burner.  The Linux drive is not listed.
I guess the question now is why isn't the Linux drive listed?

---

### Post by cbow12 on 2007-01-25
More intrigue:
I went into cmos settings and reset defaults.  Then I selected the Linux drive as the primary boot drive.  Now under boot drive priority, I could set the Linux drive, but no sign of the Win Drive anymore!  I saved and rebooted and it booted directly into Ubuntu! This is what I am using to write this post.
Now, I have to see if I can get it to boot back into Windows on the SATA drive.
If only I could select my preference at boot-up so I wouldn't have to change the cmos settings to do this.
Any suggestions?

---

### Post by Tomosaur on 2007-01-25
Sounds like something went wrong installing grub. Try this in the Ubuntu command line:
```

sudo aptitude install grub
```

Grub is a bootloader which sits on the MBR and allows you to choose which OS to boot to upon turning on your computer. It's normally installed by default, but if it's not showing up, it must have gone wrong somewhere.

---

### Post by cbow12 on 2007-01-25
OK, I did this.  It just boots into Ubuntu only now.

---

### Post by Tomosaur on 2007-01-25
Does the grub menu screen show? If so, please paste the output of the following commands (from the terminal):

```

sudo fdisk -l

```

and

```

cat /boot/grub/menu.lst

```

---

### Post by confused57 on 2007-01-25
If **sudo fdisk -l** shows your Windows drive, adding an entry to your /boot/grub/menu.lst may enable you to boot Windows:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by cbow12 on 2007-01-26
Here is the results of sudo fdisk -l:

~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14216   114189988+  83  Linux
/dev/hda2           14217       14593     3028252+   f  W95 Ext'd (LBA)
/dev/hda5           14217       14593     3028221   82  Linux swap / Solaris

The other command renders:

$ cat/boot/grub/menu.lst
bash: cat/boot/grub/menu.lst: No such file or directory

---

### Post by cbow12 on 2007-01-27
I couldn't get any results with the cat command, but I used the text editor to look at the grub menu.  Here is the results:

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

Does this help anyone?
I read the thread about dual boot with XP on the SATA drive and Linux on the IDE drive, but the example of grub menu looked totally different, and I was afraid to change mine for fear I would not be able to boot Ubuntu anymore.
Still looking for ideas.
PS: When booted into Ubuntu, I cannot see the SATA drive, and when booted into XP, I cannot see the Linux drive.  I can see my external USB  drive from either system if I have it turned on.

---

### Post by coolen on 2007-01-27
The commands to boot to Windows on my machine are:

title		Windows XP Home Edition
rootnoverify	(hd0,0)
chainloader	+1
boot

If you can figure out what to change (hd0,0) to, you should be right. So, is your Windows sitting on a different hard drive entirely?

---

### Post by cbow12 on 2007-01-29
Yes, XP is on the SATA drive, and Ubuntu is on the primary IDE drive.  The secondary IDE drive is a DVD burner.  I also have a USB external drive that I use for back-ups, but it isn't always on.  When it is on, I can see that drive from either operating system.
As it is right now, I can boot into Windows and the system doesn't even see the IDE drive.  If I go into the cmos setup, I can change the IDE drive to the primary boot drive, then the system reads the grub file and boots into ubuntu, but doesn't see the SATA drive.
I have to go into the cmos setup and manually change the target boot drive each time I want to switch back and forth.
What I want is a menu option each time I boot to go into XP or Ubuntu, whichever I choose (without changing the cmos setup.)
I'm wondering if Boot Magic would work here?

---

### Post by cbow12 on 2007-02-07
bump:
I believe I am beginning to answer my own problem:
It turns out that the adapter I installed to operate my SATA drive is only Windows compatible.  Therefore Linux can't see the drive.
The solution would be to get a controller that is  compatible, or get a motherboard that has SATA support.
At least that is the way it appears at this point.

---

