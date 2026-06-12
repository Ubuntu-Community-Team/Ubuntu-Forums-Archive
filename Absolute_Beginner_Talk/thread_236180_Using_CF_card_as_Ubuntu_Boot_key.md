---
title: "Using CF card as Ubuntu Boot key?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by TMR on 2006-08-14
Dear All,

I wonder if you can help me get the following dual-boot behaviour?
 a) if CF card is in PC, boot using GRUB, offer O/S choice
 b) if no CF card in PC, boot using original 1st disk MBR into windows XP?

I have 
a)  160Gb SATA drive in 3 partitions
      6Gb FAT32 Vendor Windows XP Recovery Partition
     20Gb NTFS Windows XP System
    124Gb NTFS Windows XP User Data

b)   80Gb IDE drive in 2 partitions
      2Gb Swap
     78Gb Ext3 mounting /

c)   32Mb CF card (detected as /dev/sdd during install).

I can set the PC to boot from CF first if present, then 160Gb drive.  At the moment I have GRUB on MBR of main drive but would like it to work from CF card, so I can restore the 160Gb to the vendor supplied configuration (and hence in support).

I have got an Ext2 formatted partition on the CF, mounting as /boot, but grub-install /dev/sdd doesn't seem to do anything.  Do I have to copy /boot from the PC to the CF?  And then what do I put in menu.lst?

Any pointers most gratefully received.

... John

---

### Post by TMR on 2006-08-14
Just for clarification: I'm not trying to run my O/S from a Compact Flash Card --- I just want to boot from it if present and then load the kernel from my second hard disk.

TMR

---

### Post by TMR on 2006-08-14
I've figured this out ...

I'll post details later if anybody's interested ... cheers

... John

---

### Post by akniss on 2006-08-14
> **TMR said:**
> I've figured this out ...

I'll post details later if anybody's interested ... cheers

... John

I'm quite interested... let us know when you get some time!

---

### Post by TMR on 2006-08-15
The main problem, if you set your BIOS to boot from memory card (or other device) is that the drive numbering is ordered.  Not so much a problem if you want to boot ubuntu, but windows likes to be on drive 1 (hd0) AFAICS.

So, take your 'ubuntu boot device' (it could be a floppy, a CD rom or a flash card) and do

grub-install /dev/sdd
(sdd was my flash card)

Then I copied the contents of /etc/boot to the card, having formatted it with Ext2.    Then the tricky bit, editting the menu.lst.  All I did with the Ubuntu boot section was to add 1 to the hd designation, because the boot disk is now hd0, and the 1st hard drive is hd1.  However, the windows sections required these 'map' commands to swap hd1 and hd0 back over, or windows wouldn't boot:

===================================================
# This is the vendor Win XP partition
title		Microsoft Windows XP Home Edition
map		(hd0) (hd1)
map		(hd1) (hd0)
root		(hd1,1)
savedefault
makeactive
chainloader	+1

# This is the vendor recovery partition
title		HP Windows XP Recovery Partition
map		(hd0) (hd1)
map		(hd1) (hd0)
root		(hd1,0)
savedefault
makeactive
chainloader	+1
=========================================================

So now I've got a machine which is exactly as the vendor intended except it has the bios set to boot primarily from flash card, and has a second (IDE) drive in addition to the SATA with win XP on it.

If the flash card is in, it boots linux, on the second HDD.  If the flash card is out it goes straight into Win XP and nobody would guess there is a superior O/S in the machine (except I've got ExtIFS in windows, so can see the Ubuntu drive :-)

. . . TMR


Apologies if this isn't clear --- let me know if you want to do something similar and I'll help if I can.

---

