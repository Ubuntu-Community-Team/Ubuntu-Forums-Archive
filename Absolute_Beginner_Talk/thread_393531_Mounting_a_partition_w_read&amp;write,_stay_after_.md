---
title: "Mounting a partition w/ read&amp;write, stay after reboot, appear on desktop"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by ecko_blue on 2007-03-25
I've used linux for the 1st time this weekend, chose ubuntu as my distro and installed it as a dual-boot with WinXP Home on my 3yr old Dell PC with 80GiB HDD space. I've managed with some google searches and a bit of help from some friends on another forum, I managed to access the Internet via PPPoE, compile 2 apps from tar.gz, and... well those are my accomplishments :P

To avoid a re-install to get this working I'd like to figure out a way to mount my 40GiB 'Media' partition (ext2) to be used under both linux and WinXp, but mostly linux. It needs to stay mounted after a reboot, be accessable from my desktop and keep read/write capability. I've managed to give it read/write with sudo chown, and mount it manually and also have it appear on the desktop, but if I reboot that all goes away.

I'm sure I can fix it up with a re-install :( But that's no good really.

If you need any additional info, please let me know; 

My fstab file: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=fcc51bcd-c32c-4fd1-ba88-1b286540c120 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=5A8C30988C30709D /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=ef72a1e2-e4d8-4ea6-a6f7-aa96898ee68d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hda5       /mnt/Media         ext3      users,umask=0007,gid=users    0       0

```

---

### Post by raja on 2007-03-25
Hello,
What is the partition that you are trying to mount? How did you mount manually? Was the last line in the fstab file added by you ? Because it seems to be a duplicate entry for mounting /dev/hda5. If you post the output of ```
mount
```, it will help.

---

### Post by ecko_blue on 2007-03-25
Hey, thanks for the reply.

Yes, the last line was put in by me. I originally has a media partition in NTFS which I couldn't write to in linux. To troubleshoot I unmounted and formatted that partition to ext2, then went about trying to remount it and keep it mounted. It's one of the leftovers from my troubleshooting I suppose :P

Mount gives me:```
/dev/hda6 on / type ext3 (rw,errors=remount-ro)
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
/dev/scd0 on /media/cdrom1 type iso9660 (ro,noexec,nosuid,nodev,user=ecko)
/dev/hda5 on /mnt/Media type ext2 (rw)

```

---

### Post by raja on 2007-03-25
```
sudo gedit /etc/fstab
```

Now delete the line
```
# /dev/hda5
UUID=5A8C30988C30709D /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```

then reboot - it should work. If you want to test the fstab settings without rebooting 
```
sudo umount /dev/hda5
sudo mount -a
```
and check to see if the partition is mounted.

---

### Post by bodhi.zazen on 2007-03-25
Well almost ...

This line is not so good : > /dev/hda5       /mnt/Media         ext3      users,umask=0007,gid=users    0       0

First, if you want the disk on your desktop, mount it in /media not /mnt

Second, the options umask=0007,gid=users is for FAT/NTFS

Third, you did say this is an ext2 partition ?

Fourth, it is probably a good idea to check the fs integrity from time to time, change the last number to 2

Last, you should strongly consider converting to ext3. **Unmount the partition first**, then :

```
tune2fs -j /dev/hda5
```

There should be no data loss with that command and you should still have access form Windows.

You can use this line :

> dev/hda5       /media/Media         ext2      users,auto    0       2

Or if you convert to ext3 : 

> dev/hda5       /media/Media         ext3      users,auto    0       2

You may need to mount the partition and chmod **once**, but I doubt it as you said your permissions are OK now.

See here for info on fstab : [http://doc.gwos.org/index.php/Understanding_fstab](http://doc.gwos.org/index.php/Understanding_fstab)

---

### Post by ecko_blue on 2007-03-26
That's awesome! I rebooted to test and the media partition is very much on my desktop. Weirdly though, I now have Media and Media(2) pointing to the same location :P

In computer:/// it shows 49GB Volume: Media and separately, Media: Media(2) :o

In /media there is only one directory with the name media.


This is exactly what I wanted though(without the dupe Media icon)! :D :biggrin: 

Thanks bodhi.zazen, raja! I appreciate it.

---

### Post by ecko_blue on 2007-03-26
I hate to bump my own thread on the same day. Crazy how this site gets 10+ pages of posts in 6-7 hours. I'm wondering how I would get rid of one of the two duplicate media drives.

---

### Post by raja on 2007-03-26
I am not sure why you have a duplicate. Can you post your fstab again?

---

### Post by ecko_blue on 2007-03-26
Of course, thanks again:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=fcc51bcd-c32c-4fd1-ba88-1b286540c120 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
dev/hda5 /media/Media ext2 users,auto 0 2
# /dev/hda7
UUID=ef72a1e2-e4d8-4ea6-a6f7-aa96898ee68d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
```

And mount:```
/dev/hda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
/dev/hda5 on /media/Media type ext2 (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/scd0 on /media/cdrom1 type iso9660 (ro,noexec,nosuid,nodev,user=ecko)
```

---

### Post by raja on 2007-03-27
Sorry - I am not really sure about this. You can try deleting the media(2) -  may work.

---

