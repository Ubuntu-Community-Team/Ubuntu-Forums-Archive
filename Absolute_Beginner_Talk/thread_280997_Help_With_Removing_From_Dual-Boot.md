---
title: "Help With Removing From Dual-Boot"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Brother_Marquis on 2006-10-20
Folks,
I've tried Ubuntu and like it alot.  I've configured it on one PC as the sole OS.  However, I still have a PC dual-booting with Windows and want take back the disk space being used by Ubuntu.

Is there an easy and safe way to do this that will keep my Windows data intact?  I dont' want to reinstall Windows or my apps and I'm concerned that the OS loader (Grub?) will somehow mess me up to.  Grub is currently configured to boot to Windows.

---

### Post by Bachstelze on 2006-10-20
Just run GParted from a Live CD (Ubuntu's or its own) and delete all your Linux partitions, then resize the NTFS partition to suit your needs.

Then, you must restore the Windows MBR : boot from a Win XP CD, go to a recovery console and run the command *fixmbr*.

---

### Post by toxygen on 2006-10-20
you can use start->run->diskmgmt.msc {enter}
and resize the partitions to suit your needs.

---

### Post by Brother_Marquis on 2006-10-20
Say I did resize using disk mangler...how would the PC boot after rebooting?  Would Grub still be present and would there be a problem?

---

### Post by toxygen on 2006-10-21
Grub will be still present until you overwrite him with something else. I strongly do not recommend to touch /boot partition. You can delete all partitions except that one.

If you like to overwrite grub with windows bootloader just load windows install cd, hit recovery console, enter admin password and then type into console

```
fixmbr
```

there you go, windows bootloader installed and you are get rid of linux. now you can delete also /boot partition

---

### Post by Herman on 2006-10-21
> Say I did resize using disk mangler...how would the PC boot after rebooting? Would Grub still be present and would there be a problem? There will be a slight problem, but only a temporory one that's easy to repair. 
In fact Grub comes in three pieces.

The smallest part of Grub is the 'IPL' in the MBR, which is more or less just a pointer to the Ubuntu partition.
It is helped by stage1_5 of grub, which is in the 15 sectors following the MBR.
The rest of the first track (63 sectors) of the hard disk is empty, and the boot sector for the Windows partition is not until right after that. (So the MBR is not part of Windows all, and is independant of it). 

The second stage of Grub is the part that lives in the Ubuntu partition which you are planning to delete. It's the part that has the Grub menu (from your menu.lst file), and does most of the work. That part will be gone all of a sudden when you delete the partition.

If you put Windows NTLDR bootloader in your MBR first, (the way toxygen suggested is one way), before you delete your Ubuntu partition, you will then just be able to boot Windows again like you used to.

If you delete the Ubuntu partition with Grub's IPL still in the MBR and then try to boot anyway, you'll get Grub error 22, and you will not be able to boot that way.
Then, you can still do as toxygen suggested, and overwrite Grub's stage1 (pointer in MBR) with Windows' stage1, you'll just be able to boot Windows again like before you installed Ubuntu.

There are more ways to do that as well, here's a page with more, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

Regards, Herman

---

### Post by Brother_Marquis on 2006-11-17
Thank you everyone.  Worked like a charm!

BTW, I still recommend Ubuntu to everyone I know and plan on building a second Ubuntu-Only PC.

---

