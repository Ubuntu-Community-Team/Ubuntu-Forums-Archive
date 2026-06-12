---
title: "Problems mounting ipod video"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by mrufino1 on 2007-11-27
I am having a strange issue- I searched the forums and tried installing ivman as recommended in one post, but that didn't seem to do anything. I can't find ivman anywhere either, file search or otherwise, although synaptic says it is installed. I have rockbox running on the ipod, although I don't think that has anythingg to do with this. Sometimes the ipod shows up, sometimes it just won't. If I then plug it into a windows machine and eject it via itunes, when I reconnect to my linux laptop, it is recognized just fine. Any ideas?

---

### Post by Nano Geek on 2007-11-27
This probably isn't the problem but it's worth a look.
Make sure that the usb is plugged firmly into your computer. Sometimes if the computer has a curved face, the plug sometimes doesn't go in properly.

---

### Post by mrufino1 on 2007-11-27
It is plugged in all the way and the cable is good. The ipod is charging and the "do not disconnect" message appears- it is just not mounting (or being recognized by ubuntu). As I said though, if I put it on a windows machine, it appears, then when I bring it back to linux, it appears just fine. I just don't want to have to run to a windows machine every time this won't mount.

---

### Post by Nano Geek on 2007-11-27
It might be that the hard-drive is failing since the problem seems to be random. 
You could try to do a fsck check on the iPod if you can mount it again.

---

### Post by mrufino1 on 2007-11-27
Every time this happens though, if I plug it into a windows machine it is recognized and then when I put it back on the linux machine it is fine.

---

### Post by mrufino1 on 2007-12-04
I still have not solved this issue, and it stopped mounting again, this time it crashed and erased rockbox again- I had to restore it now for the third time. To recap, I am sure the usb cables are good- what should I check as far as ubuntu goes to see why it is not mounting? I am currently running fsck, and using -at to hopefully find any bad sectors on the disk (or hopefully not...), after that I am stumped, as are several people I have asked. I understood that the ipod video and ubuntu were supposed to work well together as far as using it like a drive. I don't use itunes or any other software to transfer music- I just drag it onto the drive and use rockbox (when it works) to play the music. Is it possible that the ipod is not right? I bought it used on ebay but the ipod part of it seems to work fine. I am confused, and my post probably reflects that. I am not afraid t do a little work to make this work if someone an just get me pointed in the right direction. I have searched on here and hit dead ends on links I have followed (links are active, I just mean that my question still is unanswered). One suggestion was to look at the output of dmesg I tail after the ipod is connected- how would I do this?

---

### Post by cool_walking_ on 2007-12-04
Type it in a terminal/console/command prompt.

The correct command is "dmesg | tail". The | is not a capital letter I, it is the pipe character (above or near enter on US keyboards).

---

### Post by mrufino1 on 2007-12-04
mark@mark-laptop:~$ dmesg | tail
[ 5532.206905] sd 1:0:0:0: [sda] Write Protect is off
[ 5532.206909] sd 1:0:0:0: [sda] Mode Sense: 68 00 00 08
[ 5532.206911] sd 1:0:0:0: [sda] Assuming drive cache: write through
[ 5532.207736] sd 1:0:0:0: [sda] 39075372 2048-byte hardware sectors (80026 MB)
[ 5532.215811] sd 1:0:0:0: [sda] Write Protect is off
[ 5532.215814] sd 1:0:0:0: [sda] Mode Sense: 68 00 00 08
[ 5532.215817] sd 1:0:0:0: [sda] Assuming drive cache: write through
[ 5532.215828]  sda: sda1 sda2
[ 5532.227700] sd 1:0:0:0: [sda] Attached SCSI removable disk
[ 5532.227735] sd 1:0:0:0: Attached scsi generic sg0 type 0



ark@mark-laptop:~$ dmesg | tail
[ 5535.832447] Unable to identify CD-ROM format.
[ 5535.835334] FAT: invalid media value (0x2f)
[ 5535.835339] VFS: Can't find a valid FAT filesystem on dev sda1.
[ 5535.873407] hfs: unable to find HFS+ superblock
[ 5535.879679] hfs: can't find a HFS filesystem on dev sda1.
[ 5535.886002] VFS: Can't find ext3 filesystem on dev sda1.
[ 5535.892328] VFS: Can't find an ext2 filesystem on dev sda1.
[ 5535.899765] ReiserFS: sda1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda1
[ 5535.930346] XFS: bad magic number
[ 5535.930350] XFS: SB validate failed

---

### Post by cool_walking_ on 2007-12-04
hmm... nothing really wrong there. The "no filesystem" errors about sda1 are correct. sda1 is the Apple firmware partition, and it doesn't have a filesystem. Does the emergency disk mode work? To get to emergency disk mode, reset the iPod (menu+select), then straight away hold select+play.

EDIT: Can you mount the iPod manually? To do so:
```
sudo mkdir /mnt/blah
sudo mount /dev/sda2 /mnt/blah
```
and to unmount again:
```
sudo umount /dev/sda2
```

---

### Post by mrufino1 on 2007-12-04
Well, it mounts now, I will reply when it decides to not mount (hopefully never!). Would you mind subscribing to this thread so you'll know if it happens again? I really really appreciate the help you've given me so far.

---

### Post by cool_walking_ on 2007-12-04
Sure, no problem.

---

