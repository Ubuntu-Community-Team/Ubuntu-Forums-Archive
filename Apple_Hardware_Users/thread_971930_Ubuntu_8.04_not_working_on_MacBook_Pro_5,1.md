---
title: "Ubuntu 8.04 not working on MacBook Pro 5,1"
date: 2008-11-05
forum: Apple Hardware Users
---

### Post by grimreaper1377 on 2008-11-05
Hi,
 
    I just finished installing Ubuntu 8.04 using the instructions on the MacBook Pro wiki. Everything went fine, except that I can't boot into Ubuntu. If I hold the Command key when booting up, it won't recognize the partition. Disk Utility says that there is a partition, but it can't mount it. Should I try using rEFIt?

Here is what I get when running Partition Inspector:


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    432160807  Mac OS X HFS+
 3      432160808    480988933  Basic Data
 4      480988934    482942059  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    488397167  ee  EFI Protective

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

Partition at LBA 432160808:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data

Partition at LBA 480988934:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap

---

### Post by druggo on 2008-11-05
That would be a good place to start, just a question, why are you installing 8.04 when there's 8.10? 

There's a wiki, for the macbook (not the pro) which should (except for wifi i think) suit your needs.

[https://help.ubuntu.com/community/MacBook%20Aluminum]("https://help.ubuntu.com/community/MacBook%20Aluminum")

---

### Post by cyberdork33 on 2008-11-05
you need to sync the partitions with rEFIt. 
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by grimreaper1377 on 2008-11-05
> **cyberdork33 said:**
> you need to sync the partitions with rEFIt. 
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

I tried that, but when I boot into Ubuntu, I just get a black screen. Any ideas?

---

### Post by cyberdork33 on 2008-11-05
> **grimreaper1377 said:**
> ```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    432160807  Mac OS X HFS+
 3      432160808    480988933  Basic Data
 4      480988934    482942059  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    488397167  ee  EFI Protective
```

According to this, your tables are out of sync. If you have synced them, can you please post the updated report?

---

### Post by grimreaper1377 on 2008-11-05
Sure.


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    432160807  Mac OS X HFS+
 3      432160808    480988933  Basic Data
 4      480988934    482942059  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    432160807  af  Mac OS X HFS+
 3 *    432160808    480988933  83  Linux
 4      480988934    482942059  82  Linux swap / Solaris

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

Partition at LBA 432160808:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 480988934:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

---

### Post by cyberdork33 on 2008-11-05
Everything looks good... Is it actually booting, or are you just not seeing the desktop when it gets to that point?

Have you looked here:
[http://ubuntuforums.org/showthread.php?t=950515](http://ubuntuforums.org/showthread.php?t=950515)

---

### Post by grimreaper1377 on 2008-11-05
Thanks cyberdork, everything works now. I had to power down and then boot again a couple of times.

Thanks again!

---

### Post by cyberdork33 on 2008-11-05
> **grimreaper1377 said:**
> Thanks cyberdork, everything works now. I had to power down and then boot again a couple of times.

Thanks again!
Great!
Can you mark this thread as solved from the thread tools menu at the top of the page?

Thanks.

---

