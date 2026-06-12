---
title: "Grub problems on a Macbook Pro 5.5"
date: 2013-02-07
forum: Apple Hardware Users
---

### Post by tirefiremagic on 2013-02-07
New to the forum, howdy-doody everybody!

Ok, so the issue: I was installing Ubuntu on my Macbook Pro 5.5 (using the instructions found [here]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation")) and everything was going pretty dandy.  Then, I did something stupid.  While partitioning, I forgot to change the partition grub installs onto.  Instead of choosing the ext4 partition, it was left set to hd0.  I didn't realize this until after installation, either.  When I tried to boot Ubuntu, I instead got a grub-recovery command line (which I didn't really know what to do with).

Funny thing is, I can still boot OSX (with and without rEFIt; I tried un- and re-installing that, didn't change a thing).  I guess that's not the funny part.  Real funny: whenever I try changing the partitions on disk utility in OSX (I had given up in frustration, decided to just wipe out my Linux plans) I get the error "MediaKit reports no such partition".  I went in with the live cd and was able to change it around just fine (so it might have something to do with disk utility not liking linux-related things?), but when I tried to reinstall Ubuntu (taking special care about what partition I was installing grub onto) everything went smooth until it tried to install grub.  Threw an error, said it was fatal, sent a bug report, back to square one.

So I have no idea what is going on in there.  At first, I thought that the first installation of Ubuntu (the one I butterfingered) had put grub in the EFI partition, but that seems fine.  So that means it was installed in the partition "hd0".  Where the deuce is that?  Is that the partition table?  Gah!  Really wish I knew more about what I was doing.

I guess this isn't the worst thing in the world.  I have backups, still can boot into OSX, can probably reclaim that hard disk space for it, too (though disk utility's errors above are very disconcerting).  But something tells me this is going to come back and bite me if I don't try to fix whatever got broke.  I really appreciate any ideas ya'll have on the matter.

Also, some output from things:

"diskutil list" from OSX command line:
```

/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *160.0 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            127.7 GB   disk0s2
   3:                 Linux Swap                         2.0 GB     disk0s3
   4:       Microsoft Basic Data                         30.1 GB    disk0s4

```

rEFIt's Partition Inspector output:
```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    249819663  Mac OS X HFS+
 3      249821184    253818879  Linux Swap
 4      253818880    312580095  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    249819663  af  Mac OS X HFS+
 3      249821184    253818879  82  Linux swap / Solaris
 4      253818880    312580095  83  Linux

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
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 249821184:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Linux Swap
 Listed in MBR as partition 3, type 82  Linux swap / Solaris

Partition at LBA 253818880:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

```

"sudo gpt -r show disk0" again, OSX terminal
```

gpt show: disk0: Suspicious MBR at sector 0
      start       size  index  contents
          0          1         MBR
          1          1         Pri GPT header
          2         32         Pri GPT table
         34          6         
         40     409600      1  GPT part - C12A7328-F81F-11D2-BA4B-00A0C93EC93B
     409640  249410024      2  GPT part - 48465300-0000-11AA-AA11-00306543ECAC
  249819664       1520         
  249821184    3997696      3  GPT part - 0657FD6D-A4AB-43C4-84E5-0933C84B4F4F
  253818880   58761216      4  GPT part - EBD0A0A2-B9E5-4433-87C0-68B6B72699C7
  312580096       1679         
  312581775         32         Sec GPT table
  312581807          1         Sec GPT header

```

---

### Post by tirefiremagic on 2013-02-09
Agh, finally realized that was the MBR, I'm sorry guys, my bad, taken care of now.

---

