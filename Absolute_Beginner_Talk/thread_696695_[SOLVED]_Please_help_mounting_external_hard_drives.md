---
title: "[SOLVED] Please help mounting external hard drives"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by andybleaden on 2008-02-14
Hi I posted this a week ago and have got nowhere despite earlier help

[http://ubuntuforums.org/showthread.php?t=687393](http://ubuntuforums.org/showthread.php?t=687393)

I have 2 external Hdds which I can mount but not automatically since going to Gutsy

I also cannot seem to get them mounted with permission to write as they are owned by root

A print out of **mount **give this 

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hda3 on /home type ext3 (rw)
/dev/hdb1 on /media/hdb1 type ext3 (rw)
/dev/sda1 on /media/sda1 type vfat (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/sda2 type vfat (rw,noexec,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)


[B]
sudo fdisk -l[/B]

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f1e8855

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1567    12586896   83  Linux
/dev/hda2            1568        1828     2096482+  82  Linux swap / Solaris
/dev/hda3            1829        4865    24394702+  83  Linux

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9007872d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24321   195358401   83  Linux

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    c  W95 FAT32 (LBA)


**ls /media **

andy@andy-desktop:~$ ls /media
cdrom  cdrom0  cdrom1  floppy  floppy0  hdb1  sda1  sda2


I have tried change using chown commands but it does not seem to work 


Any help please as it is really confusing

---

### Post by taurus on 2008-02-14
Try

```
sudo umount /dev/sda1 /dev/sdb1
sudo mount -t vfat /dev/sda1 /media/sda1 -o umask=000
sudo mount -t vfat /dev/sdb1 /media/sda2 -o umask=000
ls -la /media
```
Can you post your /etc/fstab to see how you try to mount them in here?

```
cat /etc/fstab
```

---

### Post by andybleaden on 2008-02-14
Thank you for such quick and easy to follow guidance ( although I pasted the whole lot in at first! Doh !)  anyway .....

andy@andy-desktop:~$ sudo umount /dev/sda1 /dev/sdb1
[sudo] password for andy:
andy@andy-desktop:~$ sudo mount -t vfat /dev/sda1 /media/sda1 -o umask=000
andy@andy-desktop:~$ sudo mount -t vfat /dev/sdb1 /media/sda2 -o umask=000
andy@andy-desktop:~$ ls -la /media
total 88
drwxr-xr-x  8 andy root  4096 2008-02-14 14:49 .
drwxr-xr-x 21 root root  4096 2008-01-20 19:23 ..
lrwxrwxrwx  1 root root     6 2008-01-20 19:06 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-01-20 19:06 cdrom0
drwxr-xr-x  2 root root  4096 2008-01-20 19:06 cdrom1
lrwxrwxrwx  1 root root    45 2008-01-20 19:07 .directory -> /etc/kubuntu-default-settings/directory-media
lrwxrwxrwx  1 root root     7 2008-01-20 19:06 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2008-01-20 19:06 floppy0
-rw-r--r--  1 root root     0 2008-02-14 14:49 .hal-mtab
-rw-------  1 root root     0 2008-02-14 14:49 .hal-mtab-lock
drwxr-xr-x  5 andy andy  4096 2007-09-27 14:38 hdb1
lrwxrwxrwx  1 root root    42 2008-01-20 19:07 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwxrwxrwx 22 root root 32768 1970-01-01 01:00 sda1
drwxrwxrwx 17 root root 32768 1970-01-01 01:00 sda2


(that was weird as there was a fizzing on and off with the drives ( unmounting I guess) 

I then ran 
cat /etc/fstab
and got 
andy@andy-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=8b78bbeb-aa88-4f6c-ad39-c61236f9ac2f / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda3
UUID=cfd8583d-039e-4767-ae36-2980f6e4ffb7 /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hdb1
UUID=bbf1f71c-c8b1-4c4a-8947-e888fb229014 /media/hdb1 ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hda2
UUID=7bb7d5e0-cf56-44f8-9c55-8b0e4fe7b07f none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda1 /media/sda1 auto users,atime,auto,rw,nodev,noexec,nosuid 0 0
/dev/sdb2 <mount\040point> auto users,atime,auto,rw,nodev,noexec,nosuid 0 0
LABEL=Elements /media/sda2 auto users,atime,auto,rw,nodev,noexec,nosuid 0 0

---

### Post by taurus on 2008-02-14
The last two lines in your /etc/fstab look the weirdest!

```

/dev/sda1 /media/sda1 auto users,atime,auto,rw,nodev,noexec,nosuid 0 0
[B][COLOR="Blue"]/dev/sdb2 <mount\040point> auto users,atime,auto,rw,nodev,noexec,nosuid 0 0
LABEL=Elements /media/sda2 auto users,atime,auto,rw,nodev,noexec,nosuid 0 0[/COLOR][/B]
```
Not sure where or how you decided to add those lines but personally, I would edit /etc/fstab and replace those lines from above with these new lines.

```
/dev/sda1   /media/sda1   vfat   defaults,umask=000   0   0
/dev/sdb1   /media/sda2   vfat   defaults,umask=000   0   0
```
Save it and reboot.

---

### Post by andybleaden on 2008-02-14
Sorry I am not that fast at this 

do I paste this 
edit /etc/fstab
or this 
/dev/sda1   /media/sda1   vfat   defaults,umask=000   0   0

a combination of the two


or something else into konsole?

---

### Post by taurus on 2008-02-14
Edit /etc/fstab by typing this code below into a terminal.

```
kdesu kate /etc/fstab
```
Then, scroll down and remove these three lines at the end.

```

dev/sda1 /media/sda1 auto users,atime,auto,rw,nodev,noexec,nosuid 0 0
/dev/sdb2 <mount\040point> auto users,atime,auto,rw,nodev,noexec,nosuid 0 0
LABEL=Elements /media/sda2 auto users,atime,auto,rw,nodev,noexec,nosuid 0 0

```
Now, add these two lines to the end of that file.

```

/dev/sda1   /media/sda1   vfat   defaults,umask=000   0   0
/dev/sdb1   /media/sda2   vfat   defaults,umask=000   0   0

```
Save it and close down that editing window.  Reboot and see if you can write to both drives in /media/sda1 & /media/sda2.

---

### Post by andybleaden on 2008-02-14
Well after install gkedit and then realising it was the same as kate I went back and followed your advice. I can write to sda1 but not sda2...I note from the read out below they are both still root

andy@andy-desktop:~$ ls -la /media
total 88
drwxr-xr-x  8 andy root  4096 2008-02-14 14:49 .
drwxr-xr-x 21 root root  4096 2008-01-20 19:23 ..
lrwxrwxrwx  1 root root     6 2008-01-20 19:06 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-01-20 19:06 cdrom0
drwxr-xr-x  2 root root  4096 2008-01-20 19:06 cdrom1
lrwxrwxrwx  1 root root    45 2008-01-20 19:07 .directory -> /etc/kubuntu-defaul                                                             t-settings/directory-media
lrwxrwxrwx  1 root root     7 2008-01-20 19:06 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2008-01-20 19:06 floppy0
-rw-r--r--  1 root root     0 2008-02-14 14:49 .hal-mtab
-rw-------  1 root root     0 2008-02-14 14:49 .hal-mtab-lock
drwxr-xr-x  5 andy andy  4096 2007-09-27 14:38 hdb1
lrwxrwxrwx  1 root root    42 2008-01-20 19:07 .hidden -> /etc/kubuntu-default-s                                                             ettings/hidden-media
drwxrwxrwx 23 root root 32768 2008-02-14 16:25 sda1
drwxrwxrwx 17 root root 32768 1970-01-01 01:00 sda2


andy@andy-desktop:~$ mount -ls
/dev/hda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hda3 on /home type ext3 (rw) []
/dev/hdb1 on /media/hdb1 type ext3 (rw) []
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sda1 on /media/sda1 type vfat (rw,umask=000) [My Book]
/dev/sdb1 on /media/sda2 type vfat (rw,umask=000) [Elements]

Anything else I can try ?

---

### Post by andybleaden on 2008-02-14
Nope tried again and still the same I can now write to sda1 but not sdb1 and they are still owned by root. sdb1 is read only still..although why one changed and not the other??

Any more help at all ...I really do appreciate your time on this

---

### Post by andybleaden on 2008-02-14
aha!

I went to system settings as admin and could then for the first time change the owner of the drive to me....yippeeee!

I then closed it down and tried to write in it and it worked

I then re did this and got the following readout 

drwxr-xr-x  8 andy root  4096 2008-02-14 14:49 .
drwxr-xr-x 21 root root  4096 2008-01-20 19:23 ..
lrwxrwxrwx  1 root root     6 2008-01-20 19:06 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-01-20 19:06 cdrom0
drwxr-xr-x  2 root root  4096 2008-01-20 19:06 cdrom1
lrwxrwxrwx  1 root root    45 2008-01-20 19:07 .directory -> /etc/kubuntu-default-settings/directory-media
lrwxrwxrwx  1 root root     7 2008-01-20 19:06 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2008-01-20 19:06 floppy0
-rw-r--r--  1 root root     0 2008-02-14 14:49 .hal-mtab
-rw-------  1 root root     0 2008-02-14 14:49 .hal-mtab-lock
drwxr-xr-x  5 andy andy  4096 2007-09-27 14:38 hdb1
lrwxrwxrwx  1 root root    42 2008-01-20 19:07 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwxrwxrwx 22 andy andy 32768 1970-01-01 01:00 sda1
drwxrwxrwx 18 andy andy 32768 2008-02-14 17:13 sda2


Does that mean that next time I reboot it should still be the same....we will see ...thanks for your help taurus...looks like you have solved it ..I will mark the post as solved

---

