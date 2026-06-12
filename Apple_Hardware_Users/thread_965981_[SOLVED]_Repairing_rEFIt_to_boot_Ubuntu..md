---
title: "[SOLVED] Repairing rEFIt to boot Ubuntu."
date: 2008-11-01
forum: Apple Hardware Users
---

### Post by Mosley on 2008-11-01
I have a Macbook 4.1 which I've been using Ubuntu on for the past two months. Yesterday I decided to upgrade to Intrepid, and I was able to do this (seemingly) without a problem. I then decided to use the partition manager to turn the unpartitioned space on my drive into an ext3 partition. I believe this screwed up my rEFIt, as it no longer shows the Linux icon at startup

I tried re-installing rEFIt, but I'm still having the problem.

The rEFIt partition inspector tool gave the following output:
```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     67256359  Mac OS X HFS+
 3       67256360    184443860  Basic Data
 4      184443861    447924329  Basic Data
 5      447924330    453579209  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     67256359  af  Mac OS X HFS+
 3 *     67256360    184443860  83  Linux
 4      184443861    447924329  83  Linux

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

Partition at LBA 67256360:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 184443861:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 447924330:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap
```

Does anyone know how I can make my Macbook boot Ubuntu again? I'm not at all fond of OSX.

---

### Post by cyberdork33 on 2008-11-01
Well everything looks fine from that. Maybe you should try to reinstall grub.

Boot from the Ubuntu LiveCD, open a terminal and run 'sudo grub'.

A grub> command prompt will appear. You need to run these commands:

```
find /boot/grub/stage1
```

If that does not work, try this instead:

```
find /grub/stage1
```

The command should tell you the the partition code for where the grub supporting files are located. It should look something like (hd0,2).

For this next command, use the partition code found above.
```
root (hd0,2)
```

Then do the install to the MBR:
```
setup (hd0)
```

then you can quit and reboot:
```
quit
```

---

### Post by Mosley on 2008-11-01
Thank you so much Cyberdork! Your solution worked properly. Hopefully this thread will help out others in the future.

---

### Post by kosumi68 on 2008-11-01
Please switch the thread to solved - it will be a lot easier for people to find it, when they are looking for the solution to their problem.

Thanks!

---

### Post by cyberdork33 on 2008-11-01
> **kosumi68 said:**
> Please switch the thread to solved - it will be a lot easier for people to find it, when they are looking for the solution to their problem.

Thanks!

The option is found in the thread tools menu at the top of the page.

---

