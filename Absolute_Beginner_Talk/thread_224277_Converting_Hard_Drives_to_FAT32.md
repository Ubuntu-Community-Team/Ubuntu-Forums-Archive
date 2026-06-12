---
title: "Converting Hard Drives to FAT32"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by bamend on 2006-07-27
I've got 4 extra hard drive partitions and I was trying to use NFTS-3G but it won't mount all of the drives.  Now I've started converting them to FAT32.  How do I change my /ext/fstab to recognize the newly formated partitions?

Thanks.

---

### Post by steve.horsley on 2006-07-27
First use the command **sudo fdisk -l** to find what the partitions are called - what device names they have been given.
Second, create directories to mount them at.
Third, add lines like this to /etc/fstab, changing the device name and the mount point as appropriate:
> /dev/sda5       /mnt/F          vfat    defaults,utf8,umask=000 0       0

---

### Post by tturrisi on 2006-07-27
udo mkdir /media/NAME-OF-PARTITION
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

    * Append the following line at the end of file (where hda is your hd w/ the partition)

/dev/hda1    /media/NAME-OF-PARTITION vfat  iocharset=utf8,umask=000  0    0

    * Save the edited file

then run this command to reload fstab:  sudo mount -a

---

