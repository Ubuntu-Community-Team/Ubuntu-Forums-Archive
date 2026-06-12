---
title: "how to recover from this partition table"
date: 2008-04-13
forum: Apple Intel Users
---

### Post by FerdinandoPucci on 2008-04-13
Hi all,
I have messed up the mbr partition scheme on my macbook and I'm not able to sync it neither with refit. Here is the report from refit partiion inspector tool:

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    115490855  Mac OS X HFS+
 3      115490856    136517767  EFI System (FAT)
 4      136779919    156301454  EFI System (FAT)

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    115490855  af  Mac OS X HFS+
 3 *    115490856    136517767  83  Linux
 4              1    156301454  ee  EFI Protective

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 115490856:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 3, type EFI System (FAT)
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 136779919:
 Boot Code: Windows NTLDR
 File System: FAT32
 Listed in GPT as partition 4, type EFI System (FAT)

Linux boots but windows doesn't anymore. I think that if I get the mbr table back to a correct state I will be able to boot win again. How can I procede?

Thanks!

Ferdinando

---

### Post by cyberdork33 on 2008-04-13
i don't really see anything wrong.

Can you give more information about what happens when you attempt to boot windows? Take us step by step what you do.

---

### Post by FerdinandoPucci on 2008-04-14
Thank you for the reply.

I supposed that it is wrong to have the GPT partition start and end points different from those in the MBR table. Isn't this that gptsync corrects?

I had just updated the EFI from apple updates but it didn't installed the update since the partition scheme is MBR ([http://docs.info.apple.com/article.html?artnum=303609](http://docs.info.apple.com/article.html?artnum=303609)).

When I boot windows GRUB starts and shows the linux and windows partition. Once I choose windows(XP), its splash screen appears and suddenly the system reboots. 

Linux boots fine.

any suggestion on how to procede?

thanks again
Ferdinando

---

### Post by cyberdork33 on 2008-04-14
> **FerdinandoPucci said:**
> Thank you for the reply.

I supposed that it is wrong to have the GPT partition start and end points different from those in the MBR table. Isn't this that gptsync corrects?

I had just updated the EFI from apple updates but it didn't installed the update since the partition scheme is MBR ([http://docs.info.apple.com/article.html?artnum=303609](http://docs.info.apple.com/article.html?artnum=303609)).

When I boot windows GRUB starts and shows the linux and windows partition. Once I choose windows(XP), its splash screen appears and suddenly the system reboots. 

Linux boots fine.

any suggestion on how to procede?

thanks again
Ferdinando
I see what you are saying now. The EFI updates require an EFI partition to store the data. 

I'd say it is a problem with windows because the partition format has changed (or something like that). It is crashing and reboots because of this. You might be able to change the boot.ini file somehow, but if push comes to shove, you might just pull the data off that you need and reinstall.

You can try looking at the partition table with parted (or gparted) to see if things are screwy there. If nothing else, fdisk pays no attention to the GPT, so it will read/modify ONLY the MBR

---

### Post by russo.mic on 2008-04-14
Well Hold the phone,  before you start reinstalling,  why don't you just try booting off the Vista CD, repair option, select the recovery console and type:

bootrec /fixmbr
bootrec /fixboot

This will attempt to restore the vista bootloader.  Now, this could mean that you would be able to restore the Vista partition, but not be able to boot into the Linux!  Still grub is pretty easy to restore.  

I'm pretty sure that if you reinstall Vista, you'll render linux unable to be booted into until you restore grub anyway.  

Just giving you some choices!

Good Luck!  Post your results.

Russo

---

### Post by ronocdh on 2008-04-16
I'm with russo. I've done similar things to my PTs before and been able to resolve them most of the time by reinstalling the MBR via Windows (XP) disc, then resetting up GRUB from an Ubuntu CD.

---

### Post by mrsteveman1 on 2008-04-16
Fixmbr only updates the boot code in the first 446 bytes of a drive. OS X ignores the executable code in the MBR anyway unless all other boot options have been exhausted, and fixmbr doesn't actually touch the partition entries so it won't fix those if thats what you need to do.

When the tables are so out of sync that gptsync wont fix it, the best thing to do is perhaps to zero out the mbr and get something to write a new one, or write one yourself manually with fdisk.

I've had to do this before, it's not the easiest thing in the world but it works. If you don't want to do that and if the tables are significantly screwed up, it would be easier to just save your data and reinstall everything.

---

