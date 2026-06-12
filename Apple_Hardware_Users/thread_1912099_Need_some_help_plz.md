---
title: "Need some help plz"
date: 2012-01-20
forum: Apple Hardware Users
---

### Post by andrix10 on 2012-01-20
K i partitioned my hdd to 1g and 15g, installed refit, got the newest ubuntu version, burned it to a cd with lowest speed possible, tried to install it and it failed

it says,  unable to find a medium containing a live file system

maybe because i have windows installed too?

macbook pro 8.1, late 2011

---

### Post by andrix10 on 2012-01-20
k so i tried booting it from the cd, same thing happened

---

### Post by allebone on 2012-01-20
What does your partition layout look like? Screenshot (From booted livecd installer)

pete

---

### Post by andrix10 on 2012-01-20
i kinda restored them back because i have to reinstall windows, and i cant because it needs a whole mac partition

and my previous windows wouldnt show up in refit for some reason after i tried installing ubuntu

---

### Post by allebone on 2012-01-20
It would be difficult to help you without more information regarding the partition layout.

---

### Post by mlentink on 2012-01-20
> **andrix10 said:**
> i partitioned my hdd to 1g and 15g

If you have windows too, you certainly did not partition to 1G and 15G. Neither OSX nor Windows would fit in 1G.
So what does your partition layout look like?

A quick look at the website (i had never heard of refit and don use macs) tells me that it lacks partioning tools.  I use GParted (on the Ubuntu Live CD).

---

### Post by andrix10 on 2012-01-20
K I used bootcamp for my windows partition of 120g, for Ubuntu I used disk utility, comes with Mac os

---

### Post by allebone on 2012-01-20
> **andrix10 said:**
> K I used bootcamp for my windows partition of 120g, for Ubuntu I used disk utility, comes with Mac os

This is not helpful information. You have not provided a way for us to know your current partition layout via a screenshot or somesuch.

Pete

---

### Post by andrix10 on 2012-01-20
> **allebone said:**
> This is not helpful information. You have not provided a way for us to know your current partition layout via a screenshot or somesuch.

Pete
Maybe I can find the info in the logs in the partition program that came with refit, if I do ill post it

But shouldn't it load off the cd when I just wanna try it even without partitions?

---

### Post by allebone on 2012-01-20
> **andrix10 said:**
> Maybe I can find the info in the logs in the partition program that came with refit, if I do ill post it

But shouldn't it load off the cd when I just wanna try it even without partitions?

It depends on the installation cd you are using.

---

### Post by andrix10 on 2012-01-20
I just dled the ISO and used Nero to burn it to a cd

---

### Post by allebone on 2012-01-20
I don't feel that you are providing enough verbose information for me to adequately help you with this issue. Unfortunately I will no longer monitor or reply to this thread. Hopefully someone else with more patience will attempt to help you. Sorry it didn't install or work out.

Kind regards
Pete

---

### Post by andrix10 on 2012-01-20
dont know wat u men by wat kind of cd im using

---

### Post by andrix10 on 2012-01-20
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    721112743  Mac OS X HFS+
 3      721112744    722382279  Mac OS X Boot
 4      722382848    976773119  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    721112743  af  Mac OS X HFS+
 3      721112744    722382279  ab  Mac OS X Boot
 4 *    722382848    976773119  07  NTFS/HPFS

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 721112744:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot
 Listed in MBR as partition 3, type ab  Mac OS X Boot

Partition at LBA 722382848:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 07  NTFS/HPFS, active

thats wat it says right now

---

