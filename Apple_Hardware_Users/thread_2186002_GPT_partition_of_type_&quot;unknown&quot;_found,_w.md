---
title: "GPT partition of type &quot;unknown&quot; found, will not touch this disk"
date: 2013-11-05
forum: Apple Hardware Users
---

### Post by carson.sears29 on 2013-11-05
Hello I am hoping to get some help with a problem I have been having installing ubuntu on my Macbook Pro I am pretty new to all this and I am getting pretty frustrated trying to figure this out. I was able to make the CD boot it with the help of rEFit install ubuntu 13.10 and then restart my computer after installation. I then went into the rEFit partition inspector tool to verify my partitions and I came up with the error message "GPT partition of type "unknown" found, will not touch this disk." I have tried various things like gdisk and gptsync and had a hard time figuring out both and still no solution. 

this is what i am looking at and not sure how to proceed.


*** Report for internal hard disk ***


Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    887782839  Mac OS X HFS+
 3      968568832    976771071  Linux Swap
 4      887783424    887785471  GRUB2 BIOS Boot
 5      887785472    968568831  Unknown


Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    887782839  af  Mac OS X HFS+
 3      968568832    976771071  82  Linux swap / Solaris
 4 *    887783424    887785471  83  Linux


MBR contents:
 Boot Code: GRUB


Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)


Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+


Partition at LBA 968568832:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Linux Swap
 Listed in MBR as partition 3, type 82  Linux swap / Solaris


Partition at LBA 887783424:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type GRUB2 BIOS Boot
 Listed in MBR as partition 4, type 83  Linux, active


Partition at LBA 887785472:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 5, type Unknown



Thank you in advance for any help you can offer.

---

### Post by oldfred on 2013-11-05
Not sure how it works with a Mac.

About 2/3 way down is list of actual GUIDs:
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
 
Perhaps using gdisk you created a 8300 as the new data type and your MAC does not recognize it. The 4 digit codes seem to be a short version of the very long UUIDs.
Change type code  to 8300 with dual booting with Windows on gpt
[http://www.rodsbooks.com/linux-fs-code/index.html](http://www.rodsbooks.com/linux-fs-code/index.html)

What does gdisk show?

---

### Post by hawkmage on 2013-11-05
It looks like it could be the OS X Recovery partition.  With the introduction of OS X Lion Apple implemented a recovery partition with a minimal install of OS X so you can recover your system volume.

---

