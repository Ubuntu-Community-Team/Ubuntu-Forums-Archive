---
title: "Expanding_Ubuntu_partition"
date: 2009-08-21
forum: Apple Hardware Users
---

### Post by NielsAMD on 2009-08-21
Hello,

I'm currently running a dual boot on my macbook (OSX and Ubuntu 9.04). I need more space on the ubuntu partition and i still have 60 GiB left on the OSX partition. Is there a way i could resize that partition, without erasing data on the drive, to allocate it to ubuntu?

Thanks,
Niels

---

### Post by quixote on 2009-08-22
Assuming the OSX partition is first, followed by the ubuntu partition, it would be a nasty job to move some of the unused space to ubuntu.

But you don't need to do that, if you're willing to have three partitions.  Use gparted to turn some of that 60GB into "free" space, and then format it as ext3 or whatever suits you. You can then mount the directory(ies) from the new partition to your home directory, or wherever.  From a use standpoint, it's as if it was all one big drive.  (Well, except for some backup quirks, because some commands don't cross filesystems, but that's easy to work around.)

I don't know what the complications are for the Mac OS when it wakes up to find itself with a smaller partition.  Hopefully, someone out there has that info?

---

### Post by drs305 on 2009-08-22
Here is a link to a guide I recently wrote regarding the resizing of the Ubuntu system partition. However, it is geared toward a side by side install with Windows. As with quixote, I don't know how Macs react to resized partitions. 

In any case, the post will give you some things to consider should you decide to resize your Ubuntu partition.
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by NielsAMD on 2009-08-23
Thanks, i tried it and i think it worked. However, i cant seem to boot into Ubuntu any more. When I try to load it up it only displays GRUB, and stays that way.

Can anyone help me?

---

### Post by produnis on 2009-08-23
boot from live-cd, open a terminal and type in:


```
sudo mount /dev/sda3 /mnt  # sda3 is my ubuntu-installation
sudo mount -o bind /dev /mnt/dev 
sudo mount -t proc /proc /mnt/proc 
sudo chroot /mnt /bin/bash 
grub-install /dev/sda 
update-grub 
reboot
```

you might change the first line to something different than /dev/sda3  - depending on which is ubuntu's partition

---

### Post by NielsAMD on 2009-08-23
I let the code run on my computer for 20 minutes, and still it wasnt done, so i decided to kill the process.
On reboot, no succes in booting into linux.

---

### Post by rifak on 2009-08-23
i needed to give ubuntu more space a while ago, so this is what i did:

made a gparted live cd, boot into that
shrank os x partition, and gave it to ubuntu (this takes a loooong time because its moving data to the beginning of the newly made free space)
then boot into the ubuntu live cd to update grub by using these steps
[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)

then thats it. restart and you should be good

---

### Post by NielsAMD on 2009-08-23
Ignore this, already receiving help. How can i remove this post?

---

### Post by NielsAMD on 2009-08-24
Hi i tried using this tut:
[http://maketecheasier.com/how-to-res...ntu/2008/04/11]("http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11")

However on the step where you are supposed to enter this command i get two options to choose from.
 
find /boot/grub/stage1

It results in:
(hd0,2) and hd(0,3)

Which am i supposed to choose?

Thanks

---

### Post by NielsAMD on 2009-08-24
Okay i chose (hd0,3) as root, however, my problem still exists. Can someone help me with this?

Do i need to reinstall ubuntu?

---

