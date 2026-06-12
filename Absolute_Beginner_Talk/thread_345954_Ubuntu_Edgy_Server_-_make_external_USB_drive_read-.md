---
title: "Ubuntu Edgy Server - make external USB drive read-write"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by calenti on 2007-01-25
Hi there. I just got a new external USB drive. I want to share it via Samba with a couple of XP boxes for shared backups, etc. I thought I had it configured correctly but it's not working as I expected.

Here's what I did :

1. Formatted external drive as single 250 GB partition, showed up as /dev/sda. Created /dev/sda1 and formatted using mkfs.vfat.

2. Mounted on /mnt/mybook250 with

<code> mount -t auto /dev/sda1 /mnt/mybook250 </code>

3. Installed and configured Samba and shared /mnt/mybook250.

4. Accessed /mnt/mybook250 share from XP machine, did some test file put/get.

5. Started overnight backup.

6. Came back next morning and my server was out of space - /mnt/mybook250 was not actually attached to the external drive, it was still using the server's HD.

7. So now I'm hosed - I have files in /mnt/mybook250 so I can't mount /dev/sda1 to it because I need those files on the filesystem which are currently in the /mnt/mybook250 folder.

8. So I created a new mount point: /mnt/usbdrive. Figured I'd mount the USB drive on a new mount point and copy the files. To make it load at boot I added the reference to /etc/fstab (second from last)
 
sudo more /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1 -- converted during upgrade to edgy
UUID=76770b05-ea46-40cf-b0b6-39a74a3ce5ea / ext3 defaults,errors=remount-ro 0 1
# /dev/hdd5 -- converted during upgrade to edgy
UUID=a9c8eafb-4bf7-4007-9d84-920f06bd7572 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1 /mnt/usbdrive auto rw,user,auto 0 2
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

8. But, when I reboot /dev/sda1 is not mounted

(post-reboot)
/mnt$ mount

/dev/hdd1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)

but I can mount it:

$ sudo mount -a
$ mount
/dev/hdd1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda1 on /mnt/usbdrive type vfat (rw,noexec,nosuid,nodev)


9. But even when it's mounted,  I can't change permissions, or add directories to it.

/mnt$ ls

drwxr-xr-x  5 root root   4096 2007-01-24 23:24 .
drwxr-xr-x 21 root root   4096 2006-11-05 19:10 ..
drwxrwxrwx  2 root samba  4096 2007-01-24 22:24 archive
drwsrwsrwt  8 root samba  4096 2007-01-24 23:04 mybook250
drwxr-xr-x  5 root root  16384 1969-12-31 18:00 usbdrive

/mnt$ sudo chmod 777 usbdrive
/mnt$ ls -la
total 32
drwxr-xr-x  5 root root   4096 2007-01-24 23:24 .
drwxr-xr-x 21 root root   4096 2006-11-05 19:10 ..
drwxrwxrwx  2 root samba  4096 2007-01-24 22:24 archive
drwsrwsrwt  8 root samba  4096 2007-01-24 23:04 mybook250
drwxr-xr-x  5 root root  16384 1969-12-31 18:00 usbdrive



it doesn't fail, but it doesn't change the permissions so I can't copy any files to it. I can see it and mount it with Samba but not create any directories or files.

10. Also, nobody but root has access to the mounted USB drive.

Root can create a folder but can't change the permissions:

/mnt$ sudo mkdir /mnt/usbdrive/temp

/mnt$ ls -la usbdrive
total 84
drwxr-xr-x 6 root root 16384 2007-01-24 23:34 .
drwxr-xr-x 5 root root  4096 2007-01-24 23:24 ..
drwxr-xr-x 3 root root 16384 2007-01-24 22:06 archive
drwxr-xr-x 2 root root 16384 2007-01-24 22:50 nw
drwxr-xr-x 2 root root 16384 2007-01-24 23:34 temp

/mnt$ sudo chgrp samba usbdrive/temp
chgrp: changing group of `usbdrive/temp': Operation not permitted


If someone could please help me understand what I'm doing wrong so I can figure out how to:

1. Get /dev/sda1 to mount at start and be read-write at the mount point I'm specifying in /etc/fstab at any mount point;
2. make the mount read-write for users. I tried following the instructions spread out on the web but I'm obviously doing something wrong.


Appreciate any suggestions outside of RTFM unless you can suggest a specific part of the FM to R as I am kind of stumped.


TIA

---

### Post by sardion on 2007-01-25
Try changing your fstab so that /dev/sda1 has the type vfat (right now it is auto).

---

### Post by calenti on 2007-01-26
Thanks for the advice - I tried that but it didn't seem to help. I changed the file and rebooted:

~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1 -- converted during upgrade to edgy
UUID=76770b05-ea46-40cf-b0b6-39a74a3ce5ea / ext3 defaults,errors=remount-ro 0 1
# /dev/hdd5 -- converted during upgrade to edgy
UUID=a9c8eafb-4bf7-4007-9d84-920f06bd7572 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1 /mnt/usbdrive vfat rw,user,auto 0 2
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

(reboot)

~$ mount
/dev/hdd1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)


but I can still mount with -a

~$ mount -a
mount: only root can do that
~$ sudo mount -a
Password:
~$ mount
/dev/hdd1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda1 on /mnt/usbdrive type vfat (rw,noexec,nosuid,nodev)

but I still can't do anything with it

/mnt$ ls -la
total 32
drwxr-xr-x  5 root root   4096 2007-01-24 23:24 .
drwxr-xr-x 21 root root   4096 2006-11-05 19:10 ..
drwxrwxrwx  2 root samba  4096 2007-01-24 22:24 archive
drwsrwsrwt  9 root samba  4096 2007-01-25 13:10 mybook250
drwxr-xr-x  6 root root  16384 1969-12-31 18:00 usbdrive

/mnt$ sudo chgrp -R samba usbdrive
chgrp: changing group of `usbdrive/archive': Operation not permitted
chgrp: changing group of `usbdrive/nw': Operation not permitted
chgrp: changing group of `usbdrive/temp': Operation not permitted
chgrp: changing group of `usbdrive': Operation not permitted

I've tried searching but it's all happy-path stuff; how to mount a drive, how to start samba, etc. I've even tried stopping Samba and doing the chgrp  but the result is the same.

I'm really stumped. Any pointers are appreciated, even to docs or another forum to post on.

---

### Post by po0f on 2007-01-26
calenti,

The vfat filesystem doesn't support owner:group permissions.  What you'll have to do is set "gid=X" and possibly "uid=X" mount options for the filesystem, where X is the group number of samba.  To figure this out, post the output of `grep samba /etc/group` (it should be the third field, a number).

---

### Post by calenti on 2007-01-27
Thanks p0of, that helped but I still can't (1) automatically mount the volume at boot or (2) create new directories on the drive.

Here's what happened:

1. I got the samba gid (1005) from the command you listed and changed my /etc/fstab as well to this:

```
/dev/sda1       /mnt/usbdrive   vfat    rw,user,auto,gid=1005   0        2
```

I put tabs between the entries instead of spaces in case that was causing a problem.

2. Rebooted but the drive is not being mounted on start:

(after reboot)

```
coolguy@coolplace:~$ mount\

/dev/hdd1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)

```

a basic question I have is why is this not getting mounted at boot? Is there a system log I can check for errors? I looked at /var/log/messages but there's nothing about this in there - it reported detecting the hardware each time I start,tho.


3. Moving on...I can mount it with a command but it's still 755 and I can't change that, even as root.

```

coolguy@coolplace:~$ sudo mount -a
Password:

coolguy@coolplace:~$ mount
/dev/hdd1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
**/dev/sda1 on /mnt/usbdrive type vfat (rw,noexec,nosuid,nodev,gid=1005)**


coolguy@coolplace:/mnt$ ls -la
total 32
drwxr-xr-x  5 root root   4096 2007-01-26 00:22 .
drwxr-xr-x 21 root root   4096 2006-11-05 19:10 ..
drwxrwxrwx  2 root samba  4096 2007-01-24 22:24 archive
drwsrwsrwt  9 root samba  4096 2007-01-25 13:10 mybook250
drwxr-xr-x  8 root samba 16384 1969-12-31 18:00 usbdrive

coolguy@coolplace:/mnt$ sudo chmod -R 777 usbdrive

coolguy@coolplace:/mnt$ ls -la
total 32
drwxr-xr-x  5 root root   4096 2007-01-26 00:22 .
drwxr-xr-x 21 root root   4096 2006-11-05 19:10 ..
drwxrwxrwx  2 root samba  4096 2007-01-24 22:24 archive
drwsrwsrwt  9 root samba  4096 2007-01-25 13:10 mybook250
drwxr-xr-x  8 root samba 16384 1969-12-31 18:00 usbdrive
coolguy@coolplace:/mnt$


```



Second question - why is even a sudo chmod being ignored? Root is a member of the samba group. 

Root can now touch files inside the root of /usbdrive and can create dirs, but the dirs are all 755 and root can't change them. 


Thanks for the help, this improved things but I still need to understand what's going on. If you have any other ideas I'd appreciate hearing them.

---

### Post by calenti on 2007-01-28
Found a 1/2 solution - I set the umask and changed the fstab entry parms to just use "defaults" based on another UF post which I have now lost the link to. I have "exec" as well in case I want to back up unix apps on here as well. This allowed me to edit the files and make them and the root dirs 775. 

```
/dev/sda1       /mnt/usbdrive   vfat    defaults,exec,gid=1005,umask=000        0         2
```

However, my drive still does not auto-mount at boot, but I can live with that by putting a .NODRIVEMOUNTED file in the /mnt/usbdrive directory so I know when the drive has not been mounted. 

Thanks to everyone for their help, if you have a suggestion on the auto-mount I'd like to hear it.

It also turns out this machine has a second internal 17 GB hard drive, so I will next be trying to figure out how to mount and partition that  - this is an old Celeron so I don't think I will be trying dual-boot...

---

### Post by calenti on 2007-01-30
Another followup - after that change, my drive is auto-mounting. Problem solved.

---

### Post by gcmelzi on 2007-02-07
Dear Calenti, 
could you kindly confirm all what you did was to add the correct statement to /etc/fstab, please ?

I've a similar problem to solve. :lolflag: 

Thanks.
Giancarlo

---

### Post by calenti on 2007-05-23
Sorry...I gotta figure how to subscribe to my own threads. What I did was change the /etc/fstab to read

```

/dev/sda1       /mnt/usbdrive   vfat    defaults,exec,gid=1005,umask=000        0        2

```

That (and some chmod -R 660) resolved the issue for me.

---

