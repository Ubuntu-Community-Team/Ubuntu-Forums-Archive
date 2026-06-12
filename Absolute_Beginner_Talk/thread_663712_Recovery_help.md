---
title: "Recovery help"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by cdenk on 2008-01-10
Getting a Grub Loading Stage 1.5.
Grub error 15.

Here's what happened before:
This recent install of Kubuntu Gutsy is working OK, I decide to make it easier to log into root, by making another user "ROOT", with "/" as home directory. For some reason didn't work like I expected (I'm a newbie to Linux) and with User manager, deleted "ROOT", unchecking both of the boxes to delete directories (partitions ?). But it appears that everything was deleted anyway.

Is there a way to undo this mistake?  There is nothing of value on the installation other than 'apt-get" installed packages which there were many. Just would take time to rebuild.

This is a dual boot with XP. XP is OK, used Super Grub to restore it's boot. Trying to restore Linux boot ends up with the above error.

Thanking in advance.

---

### Post by dstew on 2008-01-10
Boot a LiveCD. Open a terminal, and enter the command sudo fdisk -l. That will give you a display of your partitions. If your root partition is still there, you can mount it onto the LiveCD file system, and see if the directories are intact. If your Ubuntu root directory is sda1, you can mount it like this:```
sudo mkdir /mnt/sda1
sudo mount -t ext3 /dev/sda1 /mnt/sda1
```If you don't get an error, you can see if your old root directory is intact. It would be in the /mnt/sda1 directory.

---

### Post by cdenk on 2008-01-10
Thanks for the quick reply :)

Kubuntu was loaded at sdb1 (root partition of the 2nd hd)
here's what I did, and what was returned:

knoppix@Knoppix:~$ sudo mkdir /mnt/sdb1
knoppix@Knoppix:~$ sudo mount -t ext3 /dev/sdb1 /mnt/sdb1
mount: special device /dev/sdb1 does not exist
knoppix@Knoppix:~$ sudo mount -t ext3 /dev/sda1 /mnt/sdb1
mount: special device /dev/sda1 does not exist
knoppix@Knoppix:~$ sudo mount -t ext3 /dev/sdb1 /mnt/sda1
mount: mount point /mnt/sda1 does not exist
knoppix@Knoppix:~$

I'm assuming that all is lost, and I need to start from scratch :(  Probably won't have to do the partitions, but at that point should format the partitions, to start with a clean area, and not that difficult to do. Glad I didn't migrate over from XP yet, need to get some experience, and the links for the documentation are at local copy center for printing, he does a nice job at a cheap price, better than me wasting ink cartridge.

---

### Post by dstew on 2008-01-10
What is the output of **sudo fdisk -l**?

---

### Post by cdenk on 2008-01-10
knoppix@Knoppix:~$ sudo fdisk -l

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10444    83891398+   c  W95 FAT32 (LBA)
/dev/hda2           10445       20888    83891430    c  W95 FAT32 (LBA)
/dev/hda3           20889       38913   144785812+   f  W95 Ext'd (LBA)
/dev/hda5           20889       31333    83899431    b  W95 FAT32
/dev/hda6           31334       38913    60886318+   b  W95 FAT32

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2611    20972826   83  Linux
/dev/hdb2            2612        4866    18113287+   5  Extended
/dev/hdb5            2800        4866    16603177+  83  Linux
/dev/hdb6            2612        2798     1502014+  82  Linux swap / Solaris

Partition table entries are not in disk order
knoppix@Knoppix:~$

---

### Post by cdenk on 2008-01-10
I don't know what to say ~). It appears my output has much of the same info: starts with "Device Boot ... System", and ends with "Partition table entries are not in disk order". The listing between is what I would expect, HDA1 is the XP boot, and Ubuntu was HDB1 boot, with the partitions as I had done. Appears the sample in the last reply has numerous partition boundarys that are not on a cylinder boundary. When I set up the partitions with the Kubuntu install, partition sizes were rounded off. Thats not the issue at the moment, the question is, is there something left useable from the original install.It's not that big of a thing to reinstall, though if I could do a recovery sort of thing, that would be better.

Thanks for the quick replies :)

---

### Post by dstew on 2008-01-10
Cdenk:

From your fdisk output you can see that your Linux installation is either hdb1 or hdb5. To mount the hdb1 partition onto your LiveCD file system, use these commands:```
sudo mkdir /mnt/hdb1
sudo mount -t ext3 /dev/hdb1 /mnt/hdb1
```Then the root directory of your hdb1 partition will be found in the directory /mnt/hdb1.

And for mirulmuffs: your sdc device has a bad partition table. You could try to repair it or delete the table and start over with a partition management program, like gparted.

---

### Post by cdenk on 2008-01-10
From doing: 
sudo mkdir /mnt/sda1
sudo mount -t ext3 /dev/sda1 /mnt/sda1

knoppix@Knoppix:~$ ls /mnt/hdb1
Recycled  cdrom  home    initrd.img  lost+found  mnt   root  srv  tmp  vmlinuz
bin       dev    initrd  lib         media       proc  sbin  sys  var


I was able to access what looks like the files that are intact, and if that's the case, I would think that Super Grub could fix it, but it couldn't find the files. With Super Grub I was able to repair the XP boot, but not the Kubuntu boot. I'll have to try that again, and get what the message was exactly.

With Knoppix up, and clicking on the hdb1 icon, the files were there, and I could view some of them, and others I didn't have permission.

Any ideas from here?

And yes, I was aware of the one corrupt partition, I should have stopped and backed up at the install. I will fix it as soon a I'm up and running, or do a fresh install. There is not data on that partition, so it's no big thing. Thanks for pointing it out.

---

### Post by dstew on 2008-01-11
> sudo mount -t ext3 /dev/sda1 /mnt/sda1I assume you actually did the commands I posted. If so, hdb1 does not seem to have a normal Ubuntu root directory. For example, there is no boot directory, which is where the kernel images and grub's files are stored.

Did you look at hdb5?

---

### Post by cdenk on 2008-01-11
Yes, I did the commands as suggested, and copy/paste on my previous message. hdb5 was empty, more on that below.

Using Super Grub > Fix boot of Gnu/Linux (Grub): I get:
 findf /grub/stage1
 Error 15 File not found
findf /boot/grub/stage1
error 15 ...

Then went back to the Kubuntu install disc, first as repair, got 
a shell (/bin/sh -i) was not found on your root...  with red screen
file system (dev/sdb1), but an error occured running it.

Then with install disc, ran install, formatting both swap, and /home, being careful not to touch hdb1.
still got warning about corrupt partition, in particular file: windowssystem32configsoftware.log size error. And then there was a "debootstrap warning"   /var/log/syslog
Looking at the end of that file:

chroot.c: open() failed: No such file or directory
Jan 10 10:54:06 D845-wn avahi-daemon[5244]: Failed to open /etc/resolv.conf: Invalid argument
Jan 10 10:54:06 D845-wn avahi-daemon[5244]: Files changed, reloading.
Jan 10 10:54:06 D845-wn avahi-daemon[5244]: Failed to read /etc/avahi/services.
Jan 10 10:54:06 D845-wn avahi-daemon[5245]: chroot.c: open() failed: No such file or directory
Jan 10 10:54:06 D845-wn avahi-daemon[5244]: Failed to open /etc/resolv.conf: Invalid argument
Jan 10 10:54:47 D845-wn anacron[5374]: getpwuid() error: No such file or directory
Jan 10 10:54:47 D845-wn anacron[5374]: Aborted
Jan 10 10:55:01 D845-wn /usr/sbin/cron[5408]: (CRON) STAT FAILED (/etc/cron.d)
Jan 10 10:56:51 D845-wn kdm: :0[5746]: Can't execute "/etc/kde3/kdm/Xreset": No such file or directory
Jan 10 10:56:52 D845-wn kernel: [  565.625604] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Jan 10 10:56:52 D845-wn kernel: [  565.625852] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Jan 10 10:56:52 D845-wn kernel: [  565.626048] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Jan 10 10:56:52 D845-wn kernel: [  565.890089] [drm] Setting GART location based on new memory map
Jan 10 10:56:52 D845-wn kernel: [  565.890111] [drm] Loading R300 Microcode
Jan 10 10:56:52 D845-wn kernel: [  565.890169] [drm] writeback test succeeded in 1 usecs
Jan 10 10:56:55 D845-wn kdm: :0[5748]: IO Error in XOpenDisplay
Jan 10 10:56:55 D845-wn kdm[4948]: X server for display :0 terminated unexpectedly
Jan 10 10:56:55 D845-wn kdm[4948]: Display :0 cannot be opened
Jan 10 10:56:55 D845-wn kdm[4948]: Unable to fire up local display :0; disabling.

The ATI video has been working fine.

I'm in the XP at the moment, and using windows explorer with the EXT2 add-on, looking at the Kubuntu area, looks like most is intact, except /boot is empty except of /root, both of which have no files.

Unless there is a way to repair that partition, I'm thinking, just go from the install disc, and do a fresh install including formating / and /home. The most time consuming will be installing the applications with apt-get.

Thanks much for the help again.

---

### Post by dstew on 2008-01-11
Yes, I think a new install is the way to go. The repair errors are consistent with missing directories, like /etc and /boot. It kind of looks like the hdb1 root directory is from some other linux distribution.

---

### Post by cdenk on 2008-01-11
Thanks again for the patience, and help.
Have a good day wherever you are, it's cloudy, dark, light rain 40F in Northern Ohio. :)

---

