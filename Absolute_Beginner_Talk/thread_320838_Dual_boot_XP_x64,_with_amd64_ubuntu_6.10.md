---
title: "Dual boot XP x64, with amd64 ubuntu 6.10"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by mickd1337 on 2006-12-18
Howdy.
I have a 60gb ide running winXP x64, with screwed partitioning, so i decided to install ubuntu onto my 120gb ide where 100gb is ntfs, currently 15gb ext3 and 5gb swap. I managed to get correct partitioning and formatting (i believe) using the inbuilt ubuntu partitioner and formatter. However, once finishing installation of ubuntu, it continues to a screen asking me to eject the ubuntu boot cd, so i do, and then push enter, i do this and nothing happens. Hence i am forced to reset, and loading continues straight into winxp. I told grub to install into hd1 after it defaulted to hd0, trying both failed to boot ubuntu. Could it be my cd is corrupt in some segment or if anyone has any suggestions it would be greatly appreciated.
Thanks.

---

### Post by pay on 2006-12-18
To install grub boot the liveCD and the type into the terminal ```
sudo su
mkdir /mnt/ubuntu
mount /dev/hda3 /mnt/ubuntu #change hda3 to your disc. check your /etc/fstab if unknown
mkdir /mnt/ubuntu/boot
mount /dev/hda1 /mnt/ubuntu/boot #if the /boot is on another partition, sorry last time i had it pointing to the wrong folder, try now
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
chroot /mnt/gentoo /bin/bash
env-update
source /etc/profile
export PS1="(chroot) $PS1"
aptitude install grub
nano -w /boot/grub/grub.conf

```in the new file that has opened, add something like this```
# Which listing to boot as default. 0 is the first, 1 the second etc.
default 0
# How many seconds to wait before the default listing is booted.
timeout 30
# Nice, fat splash-image to spice things up :)
# Comment out if you don't have a graphics card installed
splashimage=(hd0,0)/boot/grub/splash.xpm.gz

title=Gentoo Linux 2.6.17-r5
# Partition where the kernel image (or operating system) is located
root (hd0,0)
kernel /boot/kernel-2.6.17-gentoo-r5 root=/dev/hda3

title=Gentoo Linux 2.6.17-r5 (rescue)
# Partition where the kernel image (or operating system) is located
root (hd0,0)
kernel /boot/kernel-2.6.17-gentoo-r5 root=/dev/hda3 init=/bin/bb

# The next four lines are only if you dualboot with a Windows system.
# In this case, Windows is hosted on /dev/hda6.
title=Windows XP
rootnoverify (hd0,5)
makeactive
chainloader +1
```save and exit and then type```
grep -v rootfs /proc/mounts > /etc/mtab
grub-install /dev/hda #change your your harddrive where linux resides
```now exit and restart```
exit
cd
umount /mnt/ubuntu/boot /mnt/ubuntu/dev /mnt/ubuntu/proc /mnt/ubuntu
shutdown now -r
```

---

### Post by mickd1337 on 2006-12-18
Hey after inserting your second quote of instructions. Saving the grub.conf file give the message "[ Error writing /boot/grub/grub.conf: No such file or directory ]"... Thanks for help.

---

### Post by pay on 2006-12-18
Do you have the boot partition mounted?```
mount /dev/hda1 /mnt/ubuntu/boot
```

---

### Post by mickd1337 on 2006-12-18
I tried using hd0 again as grub specification.

... ubuntu@ubuntu:~$ mount /dev/hda1 /mnt/ubuntu/boot
mount: only root can do that

...saving the .conf file doesnt work still...

---

### Post by pay on 2006-12-18
Sorry. try```
sudo su
mount /dev/hda1 /mnt/ubuntu/boot
```

---

### Post by mickd1337 on 2006-12-18
Spewing. Thanks again for your help.


ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mount /dev/hda1 /mnt/ubuntu/boot
mount: special device /dev/hda1 does not exist

I have no idea what i am doing with these terminal operations.

---

### Post by mickd1337 on 2006-12-18
root@ubuntu:/home/ubuntu# mount /dev/hda /mnt/ubuntu/boot
mount: block device /dev/hda is write-protected, mounting read-only

---

### Post by pay on 2006-12-18
> **mickd1337 said:**
> root@ubuntu:/home/ubuntu# mount /dev/hda /mnt/ubuntu/boot
mount: block device /dev/hda is write-protected, mounting read-only
Is it a sata? sata would be sda1, ide would be either hda1 or hdc1...if you have a /boot partition at all. Check your fstab.

---

### Post by mickd1337 on 2006-12-18
i dont know how to do that fstab command. (with permission, even in root)
but in gparted, hdc1 is only partition for 60gb ide. then i have hdd1 for ntfs, hdd2 for ext3 (boot) and hdd3 for swap, in 120gb hdd. then sda1 for sata 250gb.

---

### Post by pay on 2006-12-18
Ok then, that makes it easier. Try ```
sudo su
mount /dev/hdc1 /mnt/ubuntu
mount /dev/hdd2 /mnt/ubuntu/boot
```

---

### Post by pay on 2006-12-18
And heres some more information to help you with configuring grub
> Understanding GRUB's terminology

The most critical part of understanding GRUB is getting comfortable with how GRUB refers to hard drives and partitions. Your Linux partition /dev/hda1 (for IDE drives) or /dev/sda1 (for SATA/SCSI drives) will most likely be called (hd0,0) under GRUB. Notice the parentheses around the hd0,0 - they are required.

Hard drives count from zero rather than "a" and partitions start at zero rather than one. Be aware too that with the hd devices, only hard drives are counted, not atapi-ide devices such as cdrom players and burners. Also, the same construct is used with SCSI drives. (Normally they get higher numbers than IDE drives except when the BIOS is configured to boot from SCSI devices.) When you ask the BIOS to boot from a different hard disk (for instance your primary slave), that harddisk is seen as hd0.

Assuming you have a hard drive on /dev/hda, a cdrom player on /dev/hdb, a burner on /dev/hdc, a second hard drive on /dev/hdd and no SCSI hard drive, /dev/hdd7 gets translated to (hd1,6). It might sound tricky and tricky it is indeed, but as we will see, GRUB offers a tab completion mechanism that comes handy for those of you having a lot of hard drives and partitions and who are a little lost in the GRUB numbering scheme. That was from the Gentoo Handbook.

---

### Post by mickd1337 on 2006-12-18
> ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mount /dev/hdc1 /mnt/ubuntu
mount: mount point /mnt/ubuntu does not exist
root@ubuntu:/home/ubuntu# mount /dev/hdd2 /mnt/ubuntu/boot
mount: mount point /mnt/ubuntu/boot does not exist

I wish this was easier. I just want to check out beryl first hand :P

---

### Post by pay on 2006-12-18
Well because you have an unusual partition layout thats why it isn't being autodected. ```
sudo su
mkdir /mnt
mkdir /mnt/ubuntu
mount /dev/hdc1 /mnt/ubuntu
mkdir /mnt/ubuntu/boot
mount /dev/hdd1 /mnt/ubuntu/boot
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
chroot /mnt/ubuntu/bin/bash
env-update
source /etc/profile
export PS1="(chroot) $PS1"
aptitude install grub
nano -w /boot/grub/grub.conf
```Then add```

default 0
timeout 5

title=Ubuntu Linux
root (hd3,1)
###!!!! CHANGE THE NEXT LINE. I DON'T USE UBUNTU SO  IT WILL BE DIFFERENT
# ls /mnt/ubuntu/boot may help
kernel /boot/kernel-2.6.17-gentoo-r5 root=/dev/hda3

title=Ubuntu Linux (rescue)
root (hd3,1)
###!!!! CHANGE THE NEXT LINE. I DON'T USE UBUNTU SO  IT WILL BE DIFFERENT
kernel /boot/kernel-2.6.17-gentoo-r5 root=/dev/hdc1 init=/bin/bb

title=Windows XP
rootnoverify (hd3,0)
makeactive
chainloader +1
```Save and exit. Then.```
grep -v rootfs /proc/mounts > /etc/mtab
grub-install /dev/hdc
exit
cd
umount /mnt/ubuntu/boot /mnt/ubuntu/dev /mnt/ubuntu/proc /mnt/ubuntu
shutdown now -r
```Hopefully that is right, Good luck

---

### Post by mickd1337 on 2006-12-18
thanks for help.
ill get my friend to help.
i have no idea with linux, but problem still screwed.
he can come and check it out in person.
later.

---

### Post by mickd1337 on 2006-12-18
Here are GParted and Disk Management screenies.

[[IMG]http://img478.imageshack.us/img478/4083/screenshotre0.th.png[/IMG]](http://img478.imageshack.us/my.php?image=screenshotre0.png) 

[[IMG]http://img19.imageshack.us/img19/6479/winir7.th.jpg[/IMG]](http://img19.imageshack.us/my.php?image=winir7.jpg)

](*,)

---

