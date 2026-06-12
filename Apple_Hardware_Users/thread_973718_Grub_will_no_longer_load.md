---
title: "Grub will no longer load"
date: 2008-11-06
forum: Apple Hardware Users
---

### Post by stealth17 on 2008-11-06
I have reinstalled GRUB and I still get the same error: non-system disk error press any key to restart. I have rEFIt installed and it shows OSx and the penguin. OSx loads just fine.

I have tried resyncing the GUID table with the MBR and it results in an error.

Here is my partition scheme:

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  MS Reserved
 2         409640     73547815  Mac OS X HFS+
 3       73547816     77547816  Linux Swap
 4       77547817    488395473  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1           39  ee  EFI Protective
 2 *           40       409639  c0  Unknown
 3         409640     73547815  af  Mac OS X HFS+
 4       73547816     77547816  82  Linux swap / Solaris

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type MS Reserved
 Listed in MBR as partition 2, type c0  Unknown, active

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 3, type af  Mac OS X HFS+

Partition at LBA 73547816:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

Partition at LBA 77547817:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 4, type Basic Data

```

How can I get Ubuntu to boot again? I'm sick of OSx!

Thanks in advance,
Jordan

---

### Post by tvtech on 2008-11-07
since this is a mac is this running a standard grub windows syle mbr or do you need mbr emulation seeing that it's osx and a mac?   just a question.

---

### Post by claudius753 on 2008-11-07
Newer Apple firmware for EFI Macs include BIOS and MBR emulation.

Jordan,

Can you use the Live CD to reinstall GRUB?  Your MBR and GPT seem out of whack, where is your Linux partition in the MBR emulated table?
```

Partition at LBA 77547817:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
```

Is your Linux partition, with GRUB, but it does not show up in the MBR emulated partition table.  I think that Apple's firmware only supports 4 partitions in the emulated MBR table, this partition seems like partition 5, so maybe that is the problem?  Did you try to install any other OS?  I'm not sure what this "MS Reserved" LBA 40-409639 partition is.  I'm still a newb at this Mac + Linux stuff.

---

### Post by cyberdork33 on 2008-11-07
MBR is definitely messed up. It appears to have an extra partition that is not in the GPT.

Try:

1. Boot from the Ubuntu LiveCD. install 'refit' (sudo apt-get install refit) and then run 'gptsync' and see if it will sync the partition tables. If you still get an error try:

2. Use fdisk to attempt to delete the partitions listed in the MBR table. (fdisk will only edit the MBR, not the "real" GPT). Then try syncing the partitions again. If that errors, then:

3. Check [this link]("http://ubuntuforums.org/showthread.php?t=811240") to determine how to clear all the data in the MBR. You will need to make sure you have a rEFIt install on a USB drive, or a CD in order to sync the partition tables again on startup because this will break your Mac's ability to boot from the hard drive until the MBR is fixed. once the partitions sync, then you will need to install GRUB again.

---

