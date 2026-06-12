---
title: "refit slow"
date: 2007-05-06
forum: Apple Intel Users
---

### Post by sprucio on 2007-05-06
I recently installed refit on my Macbook pro to make things easier with a triple boot system but it takes nearly 20 seconds for the menu to pop up during boot.

After checking the partition table, it looks like the NTFS partition is set to active. If anyone of you guys have this working flawlessly, would you mind posting what the refit partition table should look like?

---

### Post by Chrisj303 on 2007-05-06
This is copy/pasted from rEFIt's partition inspector from within OSX.
It's a triple boot OSX/UBUNTU/XP on a macbook.


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     84295719  Mac OS X HFS+
 3       84557864    126500903  EFI System (FAT)
 4      126500904    156301447  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     84295719  af  Mac OS X HFS+
 3       84557864    126500903  83  Linux
 4 *    126500904    156301447  0c  FAT32 (LBA)

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

Partition at LBA 84557864:
 Boot Code: LILO
 File System: ext3
 Listed in GPT as partition 3, type EFI System (FAT)
 Listed in MBR as partition 3, type 83  Linux

Partition at LBA 126500904:
 Boot Code: Windows NTLDR
 File System: FAT32
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 0c  FAT32 (LBA), active

---

### Post by sprucio on 2007-05-06
How long does it take you to get to the refit screen? Prior to installing Windows, this worked pretty past.

---

### Post by benanzo on 2007-05-06
mine takes less than 5 secs.  Same setup as chris

---

### Post by sprucio on 2007-05-06
Does anyone have any clues as to how I can fix this? I've checked the troubleshooting page on rEFIt but didn't find much that was helpful.

---

### Post by benanzo on 2007-05-07
I can't think of anything that would cause refit to start slowly.  are all your partitions recognized and after the delay do you boo ok?

---

### Post by Chrisj303 on 2007-05-07
For me rEFIt normally comes up within 1 or 2 seconds. If i have an external drive, or a CD/DVD in the machine it will somtimes take longer.

The only difference between your setup and mine is the NTFS drive partition that you mentioned, and the fact that this is active. You can easily change the active drive via qt/g parted,- i would try that first.

Good luck!
chrisj303

---

### Post by sprucio on 2007-05-07
Chris,

Isn't yours marked active on the FAT32 partition?

I did have trouble with trying to resize the volume. It hung up but it did create the other two partitions. At one point, I also had to repair the HFS partition.

Perhaps I should reinstall the entire thing (which I don't want to do but ...) by splitting the partitions prior to installing the OS?

---

### Post by Chrisj303 on 2007-05-07
My XP partition (Fat32 - /dev/sda4) IS marked active.

Sorry for any confusion, haven't been thinking straight this morning!
My Ubuntu partition (ext3 - /dev/sda3) isn't marked as active - TBH, i'm unsure of the consequences of active/inactive drive partitions.

I trust that you have checked that your tables are in sync - via the rEFIt partition tool?

If you do choose to re-install, instead of just wiping the whole thing, i would erase/reformat 1 partition at a time, then reboot inbetween to check if the problem is still there.

But if i was a betting man, i would put the problem down to the fact that your XP partition is formatted as NTFS, and that is whats slowing it down. I pretty sure that OSX dosen't handle this extension as well as fat32.
You could also have caused minor corruption to your drive, during your botched re-size, as you explained in your last post. When re-sizing, i have found that by booting of the OSX install DVD, and using the diskutility instead of terminal to be much more reliable. I also make sure that i do this on a clean drive (having backed up and formatted before).

Other than that i'm at a loss.

---

### Post by sprucio on 2007-05-07
Chris,

Thanks for all the help thus far. I'm just glad to have someone comment and help me on this issue.

I have to have NTFS on my Windows mainly because I'll be using it for my MCSE certifications. One thing I did notice was that with Linux and Windows, the laptop just starts getting loud at odd times. It does die down but I'm not sure what's causing this at all.

Not to stray off the topic too much but I will keep searching as to why rEFIt is slow. I'm really hoping it's not a NTFS related problem.

---

### Post by benanzo on 2007-05-07
I am writing a guide so I formatted my 80 GB drive and tried to set up a triple boot with as little headache as possible, using Ubuntu's defaults as best I could (like using GRUB instead of LILO like some guides say.)  I was successful.

here's my partition tables now:
```

ben@macbook:~$ sudo gptsync /dev/sda
Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     20889640  Mac OS X HFS+
 3       20889641    102809641  EFI System (FAT)
 4      102809642    156296384  MS Reserved

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     20889640  af  Mac OS X HFS+
 3 *     20889641    102809641  ef  EFI System (FAT)
 4      102809642    156296384  07  NTFS

Status: Tables are synchronized, no need to sync.

```

OS X made an EFI partition as /dev/sda1 (which I hear isn't even used for anything since OS X's boot setup comes from it's / partition (/dev/sda2).  I am experimenting with installing OS X normally then cloning it, deleting that first partition then putting OS X back on /dev/sda1 as it's root.  This would allow Ubuntu to have a swap partition, or one for backups.  Ubuntu is installed on /dev/sda3 as ext3.  WinXP is installed on /dev/sda4 as NTFS.   I formatted that partition as NTFS while I was setting up Ubuntu, in the LiveCD.  That way the Windows installer wont choke when it doesn't see anything it can use, and I certainly didn't want FAT32.

With this setup, refit presents the boot menu in less that 3 secs, longer if I have a CD/DVD in the drive (obviously).

Here's what parted says:

```

Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags  
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot   
 2      210MB   10.7GB  10.5GB  hfs+         Apple_HFS_Untitled_1         
 3      10.7GB  52.6GB  41.9GB  ext3                               boot   
 4      52.6GB  80.0GB  27.4GB  ntfs                               msftres

```

---

### Post by Chrisj303 on 2007-05-07
So you have used the NTFS filesystem for your XP partition, and rEFIt is booting quickly - that  takes my theory out of the equation for SPRUCIO's problems then.

Good luck on your experimental tripleboot!, sounds very interesting....who knows, in a few weeks, if it's goes well you could be a multi-boot-geek-legend! ;-) 

Rather than using that space as swap (hardly ever used) i would be interested in using that as a 'share' partition - very cool.
 

cheers,

chrisj303

---

### Post by ronocdh on 2007-05-08
I just wanted to add that I have no problems at all with triple boot, but my XP partition is formatted FAT32. =/

---

