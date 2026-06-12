---
title: "GRUB Hard Disk Error with Refit on Mac Mini"
date: 2007-11-10
forum: Apple Intel Users
---

### Post by kmand on 2007-11-10
I had been booting Ubuntu on a Mac Mini off of the internal disk (hd0,2) with refit and grub. This worked for quite a while and then it broke after some Linux and Mac updates.

Now I get "GRUB Hard Disk Error", when refit tries to boot off the partition. Apparently that means that grub is having trouble with the disk geometry it tries to get from the bios when it goes to stage 1.5/2.

I know that the Bios emulation is still there, and Refit thinks the GPT and MBR are in sync.

I can boot off a grub cd, which then boots from (hd0,2), but I would like to avoid this step.

Any ideas on what might have gone wrong?

---

### Post by cyberdork33 on 2007-11-10
> **kmand said:**
> I had been booting Ubuntu on a Mac Mini off of the internal disk (hd0,2) with refit and grub. This worked for quite a while and then it broke after some Linux and Mac updates.

Now I get "GRUB Hard Disk Error", when refit tries to boot off the partition. Apparently that means that grub is having trouble with the disk geometry it tries to get from the bios when it goes to stage 1.5/2.

I know that the Bios emulation is still there, and Refit thinks the GPT and MBR are in sync.

I can boot off a grub cd, which then boots from (hd0,2), but I would like to avoid this step.

Any ideas on what might have gone wrong?
Just try to reinstall grub manually.
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)

---

### Post by kmand on 2007-11-11
I've reinstalled manually several times, both from a running ubuntu and from a grub cd. Each time I get

grub> root (hd0,2)

grub> setup (hd0,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,2) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.


But then on boot "GRUB Hard Disk Error"

Is it the not fatal embeds failing that is the problem?

---

### Post by cyberdork33 on 2007-11-11
> **kmand said:**
> I've reinstalled manually several times, both from a running ubuntu and from a grub cd. Each time I get

grub> root (hd0,2)

grub> setup (hd0,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,2) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.


But then on boot "GRUB Hard Disk Error"

Is it the not fatal embeds failing that is the problem?

can you give the output of 
```
sudo fdisk -l /dev/sda
```
and
```
sudo parted /dev/sda print
```

---

### Post by kmand on 2007-11-11
fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007427

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26       18693   149946368   af  Unknown
/dev/sda3   *       18710       19458     6008624   83  Linux

 parted /dev/sda print

Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                  Flags
 1      20.5kB  210MB  210MB   fat32        EFI system partition  boot 
 2      210MB   154GB  154GB   hfs+         Customer                   
 3      154GB   160GB  6153MB  ext3         Untitled 2                 

Information: Don't forget to update /etc/fstab, if necessary.

---

### Post by inchaos on 2007-11-15
I've got the same thing except I already had Ubuntu installed and was installing OS X.

Now instead of the GRUB menu I get "HFS+ Partition Error" and I noted the same "these are not fatal" errors when I reinstalled GRUB.

Urg, I would love to not have to reinstall Gutsy again...

---

### Post by cyberdork33 on 2007-11-15
> **kmand said:**
> fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007427

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26       18693   149946368   af  Unknown
/dev/sda3   *       18710       19458     6008624   83  Linux

 parted /dev/sda print

Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                  Flags
 1      20.5kB  210MB  210MB   fat32        EFI system partition  boot 
 2      210MB   154GB  154GB   hfs+         Customer                   
 3      154GB   160GB  6153MB  ext3         Untitled 2                 

Information: Don't forget to update /etc/fstab, if necessary.
Sorry, I never replied. That all looks OK, so I am not sure what the issue might be.

---

### Post by kmand on 2007-12-02
I'm still stuck on this, and just booting off the dvd.

I'm suspicious that grub is just not connecting properly with the Mac emulated bios. My two pieces of evidence are:

1) As posted, if I try to boot from a partition on the internal disk, I get "GRUB Hard Disk Error" which means that stage1 is getting the wrong geomerty from the bios.

2) Even if I boot off the dvd, the grub interactive mode I get does not see the external usb drive. On a normal pc notebook I have, booting off the same dvd with the same external usb drive, the interactive mode sees the external drive.

It is true that when I boot from the dvd, interactive mode can set its root to the internal drive and boot from a partition there, so it must be getting something right from the bios.

Is there some diagnostic mode to grub that might reveal whats going on?

---

