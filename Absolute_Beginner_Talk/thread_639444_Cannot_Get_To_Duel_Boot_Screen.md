---
title: "Cannot Get To Duel Boot Screen"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by GMada on 2007-12-13
A couple day ago, I posted a problem here: [http://ubuntuforums.org/showthread.php?t=637713](http://ubuntuforums.org/showthread.php?t=637713) and I think that problem and this problem are related.

It all was fixed and it worked fine since. Then today, I turned on my computer and I first got 'GRUB error 17' before my duel boot screen came up (I duel boot with XP), I restarted the computer, hoping to then go into recovery mode to fix it. But then I got a new message and it's been the only message since:
"GRUB Loading Stage1.5Read Error"

I'm still very new to all this and I never really understood GRUB right from the start, but I figured I wouldn't have to cos I just use my computer as a basic personal PC.

If anyone can give any help, it will be greatly appreciated.

---

### Post by GMada on 2007-12-13
Anyone?

---

### Post by GMada on 2007-12-13
Sorry to bump again, but I'm utterly clueless on this and I need help.

---

### Post by GMada on 2007-12-13
Still bumping

---

### Post by dstew on 2007-12-13
Hi GMada. The stage 1.5 read error means that the boot loader tried to get its next piece from the hard disk, but there was a disk error. It could be that there is something wrong with the disk access, or that the sector containing the stage 1.5 file is corrupt.

Can you boot your Ubuntu system from a CD? If not, can you boot a live CD system? Then we can check out your disk.

---

### Post by jba6511 on 2007-12-13
I am not an expert with grub in any means but it sounds like you might have to use the live cd and reinstall it. I have not done this before but there are several threads on this subject. Please do not let this discourage you from ubuntu. Normally the install is a smooth process.

---

### Post by GMada on 2007-12-13
Thankyou for your reply.

I downloaded the Ubuntu ISO file and mounted it to a disk to make a live CD. However, the disk later got scratched and I had to thow it away. The ISO was backed up on a zip drive, but someone deleted it to make more space. So I'll have to download it all over again.

When it's downloaded, mounted and so on, does it run a disk scan or something? What do I do?

---

### Post by dstew on 2007-12-13
When the Live CD system is running, open a terminal and type```
sudo fdisk -l
``` If it asks for a password, just hit return. This will output a list of your disks and partitions. You can then issue a **fsck** command on the partition that is giving you trouble. You do not need to mount the partition to do a fsck.

Overall, it sounds like your disk is dying. That is why the errors are popping up kind of randomly, and once fixed, they come back. Before doing the fsck, try to mount the partition to your Live CD file system```
mkdir /hard_disk
mount /dev/sda1 /hard_disk
```assuming the disk is /dev/sda1. Then back-up your files to a CD or flash drive. **Umount** the disk, then do fsck.

---

