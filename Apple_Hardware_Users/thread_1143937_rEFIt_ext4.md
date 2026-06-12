---
title: "rEFIt ext4"
date: 2009-04-30
forum: Apple Hardware Users
---

### Post by b3nw on 2009-04-30
Hi all,

I am not able to get rEFIt to show Ubuntu as a bootable option and I think its because its ext4, is there something special I need to do to let rEFIt to see ext4 as something more than just data partition?

I've seen lots of threads but none directly on rEFIt's ability to boot from ext4.

Thanks

---

### Post by inphektion on 2009-04-30
I had originally setup my mac to boot ubuntu from an ext4 /boot using refit.  Just installed grub to that partition (in my case /dev/sda3) instead of the mbr and worked fine after sync'ing partition tables in the refit menu.

I did nothing special for ext4.

---

### Post by cyberdork33 on 2009-04-30
> **b3nw said:**
> Hi all,

I am not able to get rEFIt to show Ubuntu as a bootable option and I think its because its ext4, is there something special I need to do to let rEFIt to see ext4 as something more than just data partition?

I've seen lots of threads but none directly on rEFIt's ability to boot from ext4.

Thanks
since refit doesn't boot (not a bootloader) and it doesn't read anyhting from the partition's filesystem, it doesn't matter what the filesystem format is.

Make sure to sync the partition tables, and maybe you need to reinstall grub.

---

### Post by Heleen on 2009-05-13
I have the same problem.
I had Ubuntu 8.10 installed on a separate partition next to my Mac OS X and a data partition. This worked fine.
I've now installed Ubuntu 9.04 instead of 8.10 using ext4. Initially I did not install grub, but this resulted in rEFIt showing a weird icon and not booting ubuntu. I then reinstalled Ubuntu 9.04 (because I couldn't after install grub, for some reason) and I installed grub to the / ubuntu partition (sda4 in my case). I now see a Tux icon in rEFIt, but it still won't boot the partition. 
When I click on the partition manager in rEFIt it says it does not need to sync. In the MBR table it shows it says the 4th partition is Linux which is correct. But in the partition table above that (can't recall what that's called) it says it's data. It does recognise the 5th as swap though.

I hope someone can help me with this.
Thanks!
Heleen

---

### Post by cyberdork33 on 2009-05-13
what happens when you try to use the tux icon? any errors shown?

---

### Post by Heleen on 2009-05-14
When I click on the Tux logo a new white screen with a small Tux in the middle appears. And then nothing happens, it just stays white with the Tux. I have to manually turn off the laptop and then turn it back on to get back to rEFIt and start Mac OS X.
I've updated rEFIt to 0.13, but that didn't make any difference.
This is the partition table from the partition inspector:
```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    146948135  Mac OS X HFS+
 3      147212288    462706687  Mac OS X HFS+
 4      462968832    485500364  Basic Data
 5      485500365    488392064  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    146948135  af  Mac OS X HFS+
 3      147212288    462706687  af  Mac OS X HFS+
 4 *    462968832    485500364  83  Linux

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

Partition at LBA 147212288:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Mac OS X HFS+
 Listed in MBR as partition 3, type af  Mac OS X HFS+

Partition at LBA 462968832:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active

Partition at LBA 485500365:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap


```
It says that it doesn't need syncing. I tried calling gptsync.efi in the EFI shell, but that is exactly the same as calling the partition manager.
I'm going to see if there's a way to sync the tables even if it says it doesn't need to. I have no idea what else there is I could try. Maybe reinstalling on EXT3, see if that at least works, although I'm not sure if that's the problem.

Thanks for the reply!

Edit: I've tried to find out how I can manually force rEFIt to sync the tables, but I can't find how to do it if it is possible at all.

---

### Post by cyberdork33 on 2009-05-14
no need to sync, they are already in sync.

I think the issue may be that the Linux partition is marked as bootable in the MBR table. I think it should be set to the OSX partition.

---

### Post by Heleen on 2009-05-15
I've tried changing the boot flag from the Linux partition to the Mac partition with GParted on the live CD, but the flag was already on the Mac partition. I changed them around and back and when I load the partition manager in the rEFIt boot menu the A star is now on partition 2. I'm not sure if it was before, because when I use the partition manager that comes with the rEFIt install dmg it's still on partition 4.
Anyway, I've tried booting Linux again, but I still have the same problem as before. I'm really considering just reinstalling Linux with ext3 to see if that works. Unless someone has any other ideas.

Thanks again for the support so far!

---

### Post by b3nw on 2009-05-16
> **cyberdork33 said:**
> since refit doesn't boot (not a bootloader) and it doesn't read anyhting from the partition's filesystem, it doesn't matter what the filesystem format is.

Make sure to sync the partition tables, and maybe you need to reinstall grub.


This was my misunderstanding. I didn't install grub. Re-Installed with ext4 and grub and worked like a charm. Thanks!

I also noticed you can't pick restart from OSX. You must choose shutdown, or the rEFIt does not show up.

---

### Post by Heleen on 2009-05-16
> **b3nw said:**
> This was my misunderstanding. I didn't install grub. Re-Installed with ext4 and grub and worked like a charm. Thanks!

I also noticed you can't pick restart from OSX. You must choose shutdown, or the rEFIt does not show up.

Where did you install grub to? hd0 or the ubuntu (/) partition or some other partition?
I'm having issues as well and since it's now working for you I'd really like to know where you installed grub to.
Thanks!

---

### Post by Colin Rovis on 2011-03-02
There is one other problem:

The system will boot, but your mac will not recognize more than one cpu.
maybe installing grub-efi can fix the problem, ([www.rodsbooks.com/ubuntu-efi/index.html](www.rodsbooks.com/ubuntu-efi/index.html)), but it boots only into grub shell and you cannot specify the linux-kernel, for grub-shell does not recognize the given paths...

so sad...
Colin

---

### Post by Colin Rovis on 2011-03-02
Unfortunately Quad-Core aren't supported by Ubuntu 10.10...

---

