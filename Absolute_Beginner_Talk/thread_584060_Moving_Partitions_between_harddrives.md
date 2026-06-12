---
title: "Moving Partitions between harddrives"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by madmatrixz3000 on 2007-10-20
I installed Ubuntu two weeks ago on my 8Gb harddrive as a test, and now I want to put it on my 30Gb with all my settings: Wine, AWN, Emerald, Advanced settings, studio deb and much else.

I have put in my 30GB on the same IDE double cable and now when I try to boot up Gusty, it goes to a blank screen then stops, I have left it over night and the same thing goes with GParted.

My question is how can I copy the data over to my 30Gb easiest.

I think that my 300Gb might be slowing Gparted so I will take it out and try again, but what suggestions do you have?

I have:
[INDENT]SATA 300Gb[/INDENT]
[INDENT]IDE 30Gb[/INDENT]
[INDENT]IDE old 8Gb[/INDENT]

---

### Post by poltiser on 2007-10-20
you might need to use alternative disk - ask cannonical - because your SATA is very big and driver can have a limit etc.
why you want to tranfer the system?
you can mount any drive and run system from an old drive...
Best regards.

PS. I have 3 systems (OSs) on SATA and 3 on IDE - I don't see the difference in speed.

---

### Post by madmatrixz3000 on 2007-10-20
i'm moving to the 30Gb so that I can use my programs in my Wine (Sims takes up almost 6Gbs for just the program, not the data.)

---

### Post by madmatrixz3000 on 2007-10-21
I moved the ext3 partition is that all I need to move from a basic install that used the entire harddrive?

---

### Post by HermanAB on 2007-10-21
Use 'dd', followed by gparted to activate the empty space.

However, you have to boot off a CDROM, so first get Knoppix, then install both the 8GB (hdb = second disk, middle of cable, slave) and 30GB (hda = first disk, end of cable, master) disks, open a console in Knoppix:
$ su
# dd bs=100K if=/dev/hdb of=/dev/hda

Long wait...
Remove the CD and 8GB disk and reboot.

Once up, run gparted and activate all the empty space in the new disk.

If anything went wrong, you still have the 8GB disk (unless you copied the wrong way!)

Cheers,

Herman

---

### Post by bodhi.zazen on 2007-10-21
You can move the partition with gparted (basically copy - paste)

You then need to mount the partition and edit /etc/fsatb and /boot/grub/menu.lst to update the new information.

You should then update or re-install grub (to the MBR)

I gave some step-by-step instructions here (although you may need to adapt) : 

[http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

---

