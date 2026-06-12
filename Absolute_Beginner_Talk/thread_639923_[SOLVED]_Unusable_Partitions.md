---
title: "[SOLVED] Unusable Partitions"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by yellowdub on 2007-12-13
Hi all, very new to Ubuntu and have a small problem with my hard disk.
After installing Ubuntu on all of the drive I decided to use Gparted to create two new partitions which it did.
Only I can't write anything to either of them.
I have an administrator and a user setup on the machine and I would like to have both new drives visible to both.
Please make any explanations simple as I have never used the Terminal and other similar posts seemed to use this in the fix.
I did try some of the fixes for the closest problems but it didn't seem to help, could have just been me doing it wrong?

---

### Post by taurus on 2007-12-13
What filesystem did you format those two new partitions?  Where do you mount them to?

Open a terminal and post the outputs of these commands here.

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Dark_Stang on 2007-12-13
You've created the partitions however you probably didn't mount them. So they're there, existing, but not being used or doing anything but holding back space. To simply mount them use the mount command.
```
sudo mount /hard/drive/partition/goes/here /folder/to/mount/to/goes/here
```

To mount the partitions automatically you should edit the fstab file at /etc/fstab
The lines you'll add will look something like this...
```
/partition/to/mount    /folder/to/mount/to   /file/system/format(ext3 or whatever)   defaults   0   0
```

For more info check out this...
[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

---

### Post by yellowdub on 2007-12-14
Taurus, I formatted then to ext3, seemed the thing to do as that is what the installation drive was!
I didn't mount them, they seem to have mounted themselves!?!
After having slept on it (reboot) I now have read and write access as the administrator so the space is not lost.

Dark_Stang, thanks for the Wikipedia link I'm going to have a good read!

Thanks.

---

