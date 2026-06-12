---
title: "Viewing mounted partition"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by bigdawg72987 on 2007-03-24
I recently mounted a windows partition to /mnt/win.  When I navigate there in the file browser to view the files it tells me I don't have the permissions to view the contents of /win.  What can I do to be able to view these files?

---

### Post by raja on 2007-03-24
Did you manually mount it or was it automatically mounted by Ubuntu automatically. Can you post the output of ```
mount
```

---

### Post by bigdawg72987 on 2007-03-24
I mounted it manually by putting into the terminal
 mkdir /mnt/win
mount -t ntfs /dev/sda1 /mnt/win

This is what mount gave me
 mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /mnt/win type ntfs (rw)


I would put it in a box but I don't know how :)

---

### Post by raja on 2007-03-24
So your /dev/sda1 is indeed mounted on /mnt/win. So what happens when you ```
ls /mnt/win
```

---

### Post by bigdawg72987 on 2007-03-24
permission denied unless I add the sudo prefix.  I found an article and was able to go into nautilus under sudo but all the files in /mnt/win still displayed a padlock near their icon.  And I wasn't able to copy files from there.

---

### Post by raja on 2007-03-24
You dont have rights to view the files as an ordinary user. You can use ```
gksudo nautilus 
```to navigate the directory. Why is the partition not mounted automatically by Ubuntu ? Can you post your /etc/fstab ?

---

### Post by bigdawg72987 on 2007-03-24
I wish it was mounted automatically.  The /etc/fstab dir is nonexistent.  Is there a way I can make the /mnt/win accessible by a non-root user?

---

### Post by raja on 2007-03-24
Can you type ```
cat /etc/fstab
``` in a terminal and post the output? Also do you intend to write to the partition or to only have read access ?

---

### Post by bigdawg72987 on 2007-03-24
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b7147517-9390-4bef-a7f5-dc6cd3d3bc47 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0a7d95cb-3e54-4629-811a-c4b11b11362c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Well as far as I know writing can corrupt the drive but if it is safe now I would like to do that.

---

### Post by raja on 2007-03-24
Try this.
1. Make a backup of your fstab - just in case..
```
cp /etc/fstab /etc/fstab.bkp
```
2. Add an entry for mounting your partition
```
sudo gedit /etc/fstab
```
Add this line to the fstab
```
/dev/sda1 /mnt/win ntfs users,gid=users,ro,umask=0222,utf8=true 0 0
```
Save and close it.
3. Now unmount and remount it
```
sudo umount /dev/sda1
sudo mount -a
```

Hopefully it should be usable now. And it should get mounted automatically on boot everytime. Please let me know if this works OK.

---

### Post by bigdawg72987 on 2007-03-24
I have not rebooted yet but I do have permission to view the files now, thanks a bunch and I will keep you posted about what happens after a reboot.  On a side note am I able to edit off the windows partition now?  And if so do I risk corrupting the drive?

---

### Post by raja on 2007-03-24
That great !
By default, you can not write to NTFS partitions in Ubuntu. NTFS-3g offers the ability to do this, but it is in beta now. I have been using it regularly now and it has been fine, so you can decide if you want to use it depending on how important your data is. Alternatives are to set up a FAT partition where you can keep shared data or to install a driver to view ext partitions in windows.

---

### Post by bigdawg72987 on 2007-03-25
I installed ntfs-3g and it works great.  And the drive does mount every time with the necessary permissions.  Thanks again.

---

