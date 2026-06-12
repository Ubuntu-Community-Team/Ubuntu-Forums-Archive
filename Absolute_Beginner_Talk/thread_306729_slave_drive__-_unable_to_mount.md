---
title: "slave drive  - unable to mount"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by meteora184 on 2006-11-25
i set up a slave drive, which i can view files and such in knoppix.  but i try opening it saying - 7.9 GB Volume - and it says its unable to mount.

how would i be able to see and edit my files?

---

### Post by taurus on 2006-11-25
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by bodhi.zazen on 2006-11-25
What is the error message? What file system (FAT, ext3) ??

Try:```
sudo mkdir /mnt/slave
sudo mount /dev/hdb1 /mnt/slave
```

---

### Post by meteora184 on 2006-11-25
well that code works, but it won't actually let me save to the harddrive.  i honestly don't know what type it is, but i wouldn't mind reformatting it to something else now.

---

### Post by taurus on 2006-11-25
Show me the output of these three commands and I will show you how to mount it with read and write each time you boot Ubuntu!

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by meteora184 on 2006-11-25
ok:
```

jake@jake-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 13.6 GB, 13676544000 bytes
255 heads, 63 sectors/track, 1662 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1590    12771643+  83  Linux
/dev/hda2            1591        1662      578340    5  Extended
/dev/hda5            1591        1662      578308+  82  Linux swap / Solaris

Disk /dev/hdb: 8447 MB, 8447459328 bytes
240 heads, 63 sectors/track, 1091 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1091     8247928+   b  W95 FAT32


jake@jake-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


jake@jake-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              12G  2.8G  8.6G  25% /
varrun                189M   92K  189M   1% /var/run
varlock               189M  4.0K  189M   1% /var/lock
udev                  189M  104K  189M   1% /dev
devshm                189M     0  189M   0% /dev/shm
lrm                   189M   19M  171M  10% /lib/modules/2.6.15-27-386/volatile
/dev/hdb1             7.9G  4.0K  7.9G   1% /mnt/slave

```

---

### Post by bodhi.zazen on 2006-11-25
With the partition mounted:```
cat /etc/mtab
```will give you (us) the type of file system...

Without knowing the file system it is hard to advise how to get read-write access.

Oh i see. It looks like a FAT partition.

Try this:
```
sudo umount /dev/hdb1
sudo mount /dev/hdb1 /mnt/slave -o umask=000
```

---

### Post by taurus on 2006-11-25
Okay, here is...

```
sudo umount /mnt/slave
sudo cp /etc/fstab  /etc/fstab.bak
gksudo gedit /etc/fstab
```
Now, add the following line to the end of it.

```

/dev/hdb1   /mnt/slave   vfat   iocharset=utf8,umask=000  0  0

```
Save it and mount it.

```
sudo mount -a
```
Enjoy...

---

### Post by meteora184 on 2006-11-25
well i can't see the drive, but there is a folder called mnt/slave inside filesystem.

would that be my slave drive, or would it just be a folder within the filesystem.

---

### Post by taurus on 2006-11-25
If you want it to appear on your desktop, then you need to mount it to /media so replace the "/mnt/slave" with "/media/slave" in /etc/fstab.  Then, run

```

sudo mkdir /media/slave
sudo umount /mnt/slave
sudo mount -a

```

---

### Post by bodhi.zazen on 2006-11-25
> **meteora184 said:**
> well i can't see the drive, but there is a folder called mnt/slave inside filesystem.

would that be my slave drive, or would it just be a folder within the filesystem.

Both. Without the partition mounted it is "just a folder". With the partition mounted it is the partition.

If you want it on your desktop, mount it in /media ( /media/share ).

If you want fast access:```
ln -s /mnt/slave ~/slave
```

You will now have a folder in your home directory ( ~ ) that is liked (short cut) to /mnt/slave.

You can chandg the names to protect the innocent !!

---

### Post by meteora184 on 2006-11-25
> **taurus said:**
> If you want it to appear on your desktop, then you need to mount it to /media so replace the "/mnt/slave" with "/media/slave" in /etc/fstab.  Then, run

```

sudo mkdir /media/slave
sudo umount /mnt/slave
sudo mount -a

```
i entered that code, and now theres a slave folder in media, but it still isn't the drive, because slave is still in mnt.  so how would i unmount it from mnt, and redo it to media.

---

### Post by taurus on 2006-11-25
```
sudo rmdir /mnt/slave
```
What is it about drive you keep talking about?  In Linux, everything is a directory (not folder unless you come from the other OS!) so you just mount your second harddrive on /media/slave!

---

### Post by bodhi.zazen on 2006-11-25
> **meteora184 said:**
> i entered that code, and now theres a slave folder in media, but it still isn't the drive, because slave is still in mnt.  so how would i unmount it from mnt, and redo it to media.

```
sudo umount /mnt/slave
sudo umount /media/slave
sudo rm -R /mnt/slave
sudo mkdir /media/slave
```

Now edit fstab and change the entry to this:> /dev/hdb1   /media/slave   vfat   users,iocharset=utf8,umask=000  0  0

Now:```
mount /media/slave
ls /media/slave
```

---

### Post by meteora184 on 2006-11-25
ok, it works fine now, TYVM.

---

### Post by quantboy on 2007-01-13
I had the exact same problem- and was able to fix using the instructions directed.  Thanks Ubuntu community!

---

### Post by crumbum on 2007-01-15
I'm new to Ubuntu and am having similar problems adding a slave drive here is where Im at so far


[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=23154&stc=1&d=1168918177[/IMG]


[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=23155&stc=1&d=1168918177[/IMG]

---

### Post by taurus on 2007-01-15
Your slave drive, /dev/hdb1, has an ext3 filesystem, not vfat.  Therefore, you need to edit your /etc/fstab and replace the old entry for /dev/hdb1 with this new line.

```
/dev/hdb1   /media/slave   ext3   defaults   0   1
```

---

### Post by crumbum on 2007-01-15
do I need to mount and unmount again after that

---

### Post by taurus on 2007-01-15
Just reboot and that would take care of it.

---

### Post by crumbum on 2007-01-15
thanks that helped alot seems to be working now.

---

### Post by taurus on 2007-01-15
Okay.  I am outta here...

---

### Post by crumbum on 2007-01-15
I spoke to soon the drive shows up but i cant save to it. I dont seem to have permission to do anything with it.

---

### Post by Buck2348 on 2007-01-15
> **crumbum said:**
> I spoke to soon the drive shows up but i cant save to it. I dont seem to have permission to do anything with it.
Edit the new line in fstab again to:
```
/dev/hdb1   /media/slave   ext3   iocharset=utf8,umask=000  0  0
```
then
```
sudo umount /media/slave
sudo mount /media/slave
```
Now you should have read/write permission.

Buck

---

### Post by crumbum on 2007-01-16
iam getting some kind of error
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by crumbum on 2007-01-16
I changed the fstab  and unmounted but the mount command did not work

---

### Post by crumbum on 2007-01-16
anyone?

---

### Post by taurus on 2007-01-16
Please change it back to the way I have before.

```
/dev/hdb1   /media/slave   ext3   defaults   0   1
```
You just need to change permissions to /media/slave with chmod so you can write to it.

```
sudo chown **crumbum**:**crumbum** /media/slave
sudo chmod -R 755 /media/slave
```
The first command makes you the owner of the directory /media/slave, ASSUMING your log in name is **crumbum**.  If it's not, replace it with the right name.  The second command change the permissions so you, the owner of the directory, can read/write/execute while everybody else can only read/execute.

Reboot and see if you can save stuff to /media/slave.

---

### Post by crumbum on 2007-01-16
I rebooted  and the drive has mounted but its still has root as the owner of the drive

---

### Post by taurus on 2007-01-16
Post these outputs from a terminal then!

```
id
ls -la /media/slave
```

---

### Post by crumbum on 2007-01-16
uid=1000(marcus) gid=1000(marcus) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin),1000(marcus)
marcus@marcus-desktop:~$ ls -la /media/slave

---

### Post by taurus on 2007-01-16
```
sudo chown **marcus**:**marcus** /media/slave
ls -la /media
```
(Post the output of the last command here...)

---

### Post by crumbum on 2007-01-16
marcus@marcus-desktop:~$ ls -la /media
total 32
drwxr-xr-x  8 root   root   4096 2007-01-15 19:58 .
drwxr-xr-x 23 root   root   4096 2007-01-15 18:20 ..
lrwxrwxrwx  1 root   root      6 2006-12-30 22:13 cdrom -> cdrom0
drwxr-xr-x  2 root   root   4096 2006-12-30 22:13 cdrom0
drwxr-xr-x  2 root   root   4096 2006-12-30 22:13 cdrom1
lrwxrwxrwx  1 root   root      7 2006-12-30 22:13 floppy -> floppy0
drwxr-xr-x  2 root   root   4096 2006-12-30 22:13 floppy0
drwxr-xr-x  2 root   root   4096 2007-01-15 18:09 sda1
drwxr-xr-x  2 root   root   4096 2007-01-15 18:09 sda2
drwxr-xr-x  3 marcus marcus 4096 2007-01-15 18:24 slave
marcus@marcus-desktop:~$ ls -la /media

---

### Post by taurus on 2007-01-16
Now see if you can write stuff to /media/slave as marcus.

---

### Post by crumbum on 2007-01-16
thanks that did it

---

