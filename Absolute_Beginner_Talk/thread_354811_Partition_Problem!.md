---
title: "Partition Problem!"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Pathway on 2007-02-06
Hello. I'm not sure if this thread belongs in here, or even if I can be helped--but I am an absolute beginner at Linux. And I think I've screwed things up badly. I'd appreciate help, if anyone is willing.

I'd been trying to install Ubuntu 6.10 from a Live CD, using the install menu inside of Ubuntu. The problem for me, as things stand, is that I can't boot into Windows. My boot order is HD, then CD-ROM so to get the Live CD to work I just get to the boot selection menu during startup (f12). 

When I boot from the hard drive, the normal process starts, but no Windows activity occurs. The screen's black.
EDIT: I can get it to start booting from safe mode sometimes, by booting from the Live CD and then selecting the option to boot from the primary HD. But it hangs while it's loading drivers and services. 

What I think caused this: I went through the install menu most of the way fairly easily, and got to the part (step 5 or 6, I believe) where it's time to select the part of my hard drive on which I want to install Ubuntu. I selected "Manually edit partition table" because, of my remaining ~47GB, I wanted to have about half of that as free space. 

After some mucking around to figure out how the utility worked and what Ubuntu wanted of me, I created a partition of around 25GB, split into 2 logical partitions and a swap partition: around 10GB for my "/" (root) directory and 12GB for "/home,"  with maybe 1.5GB as a swap file.

I was following the advice given by many sources to keep /home separate so I could keep my settings upon reinstalls.

When I got to the actual install, Ubuntu detected errors on my partitions (even my old one) and didn't let me install. At this point I shut down and tried to boot into Windows XP Media Center Edition again, and discovered the problem.

Oh, and I ran the md5 checksum program before I booted with the Live CD. When I booted with the Live CD, I used its own menu option to check it again. It's probably fine. I ran CCleaner and defragmented my hard disk immediately before starting on the Live CD. 

Specs: Intel Pentium 4 3.2 GHz, 228 GB HD, 1 GB RAM (DDR2 I think), WinXP Media Center.

---

### Post by raul_ on 2007-02-07
What you can do is boot with the Live cd and do a 

```

fsck -f <device>

```

where device is for example /dev/hda1 /dev/hda2 etc etc. Do this on all your partitions. Hopefully it will fix the errors the installer found, and then try installing again. If this doesn't work, download Super GRUB Disk (here [http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/"))
and use it to delete GRUB from MBR

Hopefully the 1st solution will work :)

If you have any doubts, please post

---

### Post by Pathway on 2007-02-07
Thanks. I'll try that.

---

### Post by housam on 2007-02-07
I would like to ask what format you selected to the new partitions that you made.

---

### Post by Pathway on 2007-02-07
Aha, at first I was getting that it couldn't be read or doesn't represent a correct filesystem. Then I remembered that my partitions were sda1, sda2, etc. Then I remembered I had to sudo it.

I got: 

fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: 84 files, 3672/20017 clusters

then 

fsck 1.39 (29-May-2006)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda2

(because sda2 is my main partition, containing winXP:mce and all my files)

and sda3 was fine. So now I think I need to figure out how to get fsck to understand how to check NTFS. Is that correct? Or can fsck even do that?

Also, when I go to /dev/ and try to open my sda's, Ubuntu (on the Live CD at any rate) doesn't know how to look in them. I'll be trying to figure that out, along with fsck and ntfs, in the next half hour or so, but I have class at 1:20 and that takes precedence, so if anyone can help me out I'd appreciate it.

Really, all I need is to browse through sda2 (my main, 228GB partition) and copy files to my (NTFS) external hard drive. Assuming I can get the external HD to work (Western Digital 250GB) and copy my files, I'd happily nuke the computer and start over with clean installs of XP Media Center and Ubuntu. Getting to boot back into Windows is just one of the ways to solve my problem.

---

### Post by housam on 2007-02-07
Boot from the live cd and  post the out put of 
```
fdisk -l
```

---

### Post by Pathway on 2007-02-07
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       29787   239223915    7  HPFS/NTFS
/dev/sda3           29788       30393     4867695   db  CP/M / CTOS / ...

Oh, and you can assume that any time I post I'm doing it from the Live CD. That's all I have available.

---

### Post by Malac on 2007-02-07
> **Pathway said:**
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       29787   239223915    7  HPFS/NTFS
/dev/sda3           29788       30393     4867695   db  CP/M / CTOS / ...

Oh, and you can assume that any time I post I'm doing it from the Live CD. That's all I have available.
Quick(ish) fix to get you back to Windows:
Insert your Windows CD and boot from that.
Choose the option R - Repair with Recovery Console
Run ```
fixboot
``` and ```
fixmbr
```
This will however toast your Ubuntu Install but should allow you to start again.

Hope this helps.

---

### Post by housam on 2007-02-07
I see that you only have 3 partitions . one for Dell utilities and second for windows and a third partition I don't know for what - most probably for recovery ( it is a small one anyway )
It is clear that you didn't create any new partitions. So. you have to fix your windows MBR by inserting its CD .
Then we can defrag the windows partition 2-3 times before resizing it . 
We can do the resizing using the Gparted tool ( on the live cd )to create an unallocated space which can be transformed into an extended partition . that one can be devided to many logical partitions .
Ubuntu can't be installed on ntfs format. only ext3 format for the root and swap for the swap partition.

---

### Post by Pathway on 2007-02-07
I've got an OEM copy of Windows, I'm not sure if I have a disk... I am sure that it's 140 miles away if it exists (in round numbers). Though I never actually got to install Ubuntu so toasting my non-existent Ubuntu install is not a problem. Could I do it with any Windows XP disk? Surely something as simple as that wouldn't require product validation, but could I do it with a non-Media Center Edition disk? I'm sure I could find someone tech-oriented in the dorms who has an XP disk. MCE is less likely. Next time I'm home I could probably use another XP disk, or whatever recovery tools Dell (gah) did give out. I'm fairly sure my family bought a copy from the store way back in the day. But that doesn't have any bearing on my situation if I need a Media Center disk.

That does help, even if it turns out it can't resolve the situation. I'm seeing the situation more clearly now. Thank you.

---

### Post by housam on 2007-02-07
I'm not sure about using other xp edition disk . but why not trying? it may work.
Good luck

---

### Post by Malac on 2007-02-07
Any XP Home/Pro CD will do, I'm not sure about a Media Edition one but I would imagine so.
The other option is if Dell have been good and installed the Recovery Console on the hard drive try pressing F8 when you here the first boot beep and keep pressing it. You may get a menu similar to this:
[ATTACH]24757[/ATTACH]
Choose Recovery Console from there and do the steps mentioned in previous post.

Hope this helps.

---

### Post by housam on 2007-02-07
> **Malac said:**
> Any XP Home/Pro CD will do, I'm not sure about a Media Edition one but I would imagine so.
The other option is if Dell have been good and installed the Recovery Console on the hard drive try pressing F8 when you here the first boot beep and keep pressing it. You may get a menu similar to this:
[ATTACH]24757[/ATTACH]
Choose Recovery Console from there and do the steps mentioned in previous post.

Hope this helps.

OK , but this will delete his files and data coz recovery partitions always return to the factory sittings.

---

### Post by Malac on 2007-02-07
> **housam said:**
> OK , but this will delete his files and data coz recovery partitions always return to the factory sittings.
Yes, with a recovery CD but not with the Windows Recovery Console this is sort of like a crippled Command Line Interface.
Yes you could toast your system from it if you knew the commands or typed in format C: or whatever.
If he runs fixboot and fixmbr all should be well. This will not delete any of his files or data all this does is reset the boot files (ntldr, etc) and reconstruct the Master Boot Record.
It's also possible to do a Repair Install from a Windows CD which leaves your data files intact and just resets the Windows System Files but that's a whole other Thread. :)

---

### Post by housam on 2007-02-07
> **Malac said:**
> Yes, with a recovery CD but not with the Windows Recovery Console this is sort of like a crippled Command Line Interface.
Yes you could toast your system from it if you knew the commands or typed in format C: or whatever.
If he runs fixboot and fixmbr all should be well. This will not delete any of his files or data all this does is reset the boot files (ntldr, etc) and reconstruct the Master Boot Record.
It's also possible to do a Repair Install from a Windows CD which leaves your data files intact and just resets the Windows System Files but that's a whole other Thread. :)

Thanks for the info.

---

### Post by Pathway on 2007-02-07
> **housam said:**
> I would like to ask what format you selected to the new partitions that you made.

oh--didn't see your post before. i selected the default format, ext3.

thanks for all the help, i'm off to try some of the things mentioned above.

---

### Post by Pathway on 2007-02-09
Is a WinXP install disk the only place I can find the Recovery Console? I don't have a floppy drive. Or rather, it's a USB drive and it's also at home. I do have an external HD and a USB key.

---

### Post by Malac on 2007-02-09
> **Pathway said:**
> Is a WinXP install disk the only place I can find the Recovery Console? I don't have a floppy drive. Or rather, it's a USB drive and it's also at home. I do have an external HD and a USB key.
The Recovery Console is on the Original Windows CD not a floppy. If you can boot from CD then you're good to go.

---

### Post by Pathway on 2007-02-09
> **Malac said:**
> The Recovery Console is on the Original Windows CD not a floppy. If you can boot from CD then you're good to go.

Yep, I'm aware of that... I'm trying to track down a Windows CD but I'm wondering if there's another place to find it. It's not as if it's the OS itself. Can't find it yet.

---

### Post by Malac on 2007-02-10
> **Pathway said:**
> Yep, I'm aware of that... I'm trying to track down a Windows CD but I'm wondering if there's another place to find it. It's not as if it's the OS itself. Can't find it yet.The only other place is if Dell have installed it to the hard drive as part of their oem setup. To check this hit the F8 key repeatedly on boot up and see if it gives you the menu on one of my previous posts

---

### Post by Nigel Eke on 2007-02-10
> **raul_ said:**
> Do this on all your partitions.
...
If you have any doubts, please post

How can I do this on all partitions on the disk?

My PC was turned off without being cleanly shutdown.  I think there's a disk problem as a result.  I have two hard disks, one with system files, swap partition etc, and one (320Gb) with /home mounted to it.

I have badblock checked both disks - all ok.

I have fsck check the main 'file' partitions - /dev/hda1 and /dev/hde1 - both clean.

How can I check the remaining paritions on /dev/hda?  Do I need to...?

Are the commands fsck /dev/hda and /dev/hde valid?  (They both produce superblock error messages - but I'm not sure if this is a valid command anyhow)

Many thanks...

---

