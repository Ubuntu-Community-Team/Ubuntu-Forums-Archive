---
title: "[SOLVED] how do you change permissions and owners?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by caoinan on 2007-08-27
how do I change the permissions and owner of external hard drives or directories to read-write for all users? Also what is the difference in showing the hard drive as a directory in the media -File Browser and showing it as hardware in the Computer-File Browser and if I change ones owner and permissions will it change the other or do I have it change it there too? Ive tried typing in
```
 sudo chown username:group filename
```
and it just says
```
changing ownership of `/media/My Book': Read-only file system
```
but it didnt change the owner of it and Ive tried changing the permissions but it just say ```
changing permissions of `/media/My Book': Read-only file system
```
and it doesnt change the permissions either. also my external hard drives arent mounting probably can anyone tell me what to do about that

---

### Post by bobbybobington on 2007-08-27
What filesystem is it formatted as?

---

### Post by yellowband on 2007-08-27
you might have to change the settings in your etc/fstab file.

have a look at it and see how your file system is mounted:

```
 sudo gedit /etc/fstab 
```

find the line that corresponds to your external drive, and check the options column.  I forget what the defaults are but there are various options you can use like 'rw' for read-write access.  maybe somebody can post more details about this, i cant remember off of the top of my head sorry.

---

### Post by caoinan on 2007-08-27
here it what is say and I dont know which one is my hard drive  it is a 1 terabyte My Book and how do I check what its formatted as?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=14a88df4-4c03-4a67-a730-8fe3dc5962d1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c0d8e6e6-87c0-4c53-8eb0-008ea255a4c7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by Seti on 2007-08-27
what exactly do you mean 'My Book' ??? It looks to me like your entire root partition '/' is /dev/hda5 and formatted as ext3.

---

### Post by caoinan on 2007-08-27
My Book is the name of the external hard drive  and Western Digital makes it

---

### Post by Seti on 2007-08-27
Alright so its an external drive? I take it you plug it in via usb? In this case if it is working properly ubuntu should just detect it when you plug it in...an icon for it should appear on your Desktop if I am not mistaken. 
Is it a new device? If it is you will need to format it such that you can use it(ie: read and write data to it).

---

### Post by caoinan on 2007-08-27
well it actually can plug in 3 ways usb 2.0,  Firewire 400, and Firewire 800, but I have it plugged it through firewire  and it sees it and I have a bunch of files and stuff on there and it can access files and stuff its just that after several minutes of not being used it unmounts(I'm guessing I'm not sure if thats the proper term to use) and I have to turn it off and back on. I've used it in windows and it works fine in windows but I'm trying to steer myself away from using windows as much as possible.   also could someone tell me the difference between firewire 400 & 800

---

### Post by Martje_001 on 2007-08-27
I think it's formatted with NTFS. Try FAT32. Both windows & linux can deal with that...

---

### Post by Seti on 2007-08-27
Alright, well turn it off and turn it back on and then view how it is mounted;```
view /etc/mtab
``` this SHOULD show the entry for your drive. For some reason it is being unmounted at some point, THIS is what we need to fix first before we can get you using your drive properly.

---

### Post by caoinan on 2007-08-27
ok heres what it says when I type:  view /etc/mtab
```
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda1 /media/disk-1 ntfs rw,nosuid,nodev,umask=222,utf8 0 0
/dev/sdc1 /media/DellUtility_ vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0
/dev/sdc2 /media/New\040Volume ntfs rw,nosuid,nodev,umask=222,utf8 0 0
/dev/sdb1 /media/My\040Book_ ntfs rw,nosuid,nodev,umask=222,utf8 0 0

```
Can I format it to FAT32 without deleting everything and if so how do I that
also can you explain what these things are and what there doing so I can understand them better in the future

---

### Post by aysiu on 2007-08-27
If it's NTFS, try [this](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html).

---

### Post by caoinan on 2007-08-27
well I tried doing what it sayed in the article but it didnt give me a choice on what drive to make the changes to it just went straight to the window with NTFS write support  dialog and one of the choices was greyed out so I chose to do it to external harddrives but I didnt effect my My Book

---

### Post by dwhitney67 on 2007-08-27
> **caoinan said:**
> well I tried doing what it sayed in the article but it didnt give me a choice on what drive to make the changes to it just went straight to the window with NTFS write support  dialog and one of the choices was greyed out so I chose to do it to external harddrives but I didnt effect my My Book

Where is the external drive mounted???  The /etc/fstab will not tell you this.  Type "**sudo mount**" on the command line; this will tell you where all drives on your system are mounted.  Is it mounted under the /media directory?

Since you have an external drive, the choice you made with the NTFS configuration tool was correct.

Here's another question... did you use your external drive under windoze?  Did you unmount it correctly before just yanking out the firewire cable from the system?

P.S.  Lose the "My Book" moniker.  Call your drive what it is... an external drive.

---

### Post by caoinan on 2007-08-27
uh ok I'll lose the moniker. yes it is mounted under the /media directory. I did use it in windows and I never unplug it and I know to use the `safely remove hardware' feature in windows and in linux I cant eject it when I try to it says `cannot eject volume' or something like applications preventing it from ejecting but Im never even using anything in there

---

### Post by yellowband on 2007-08-27
apologies abou my earlier post, fstab wont help as its an external drive

try right clicking on the icon that pops up on your desktop when you plug it in, and select 'properties'

there should be a tab that tells you what mount options are enabled.  i still think there should be a 'rw' one there that allows you to read and write files

i had a very simiar problem with my flash drive, and this solved it for me.  don't add the option without advice from somebody more experienced here though. i ran into troubles wen i first didn't get the options i needed right.

---

### Post by caoinan on 2007-08-27
here is what it says when I check the mount under the terminal
```
/dev/sdb1 on /media/My Book type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
```
and should I change the mount point to somewhere else in the properties

---

### Post by dwhitney67 on 2007-08-27
Are you still having problems writing to your external drive?  It appears from the output you provided that it is mounted read-write... which is essential.

Try this command:
[FONT="Courier New"]
$ touch /media/My\ Book/foo[/FONT]

Was it successful or did you get a "permission denied" error?

P.S.  Because the volume on your drive has a space in its name ("My Book"), the \ is needed in the command above.  The easiest thing to do is use the tab-key for filename completion as you type.

---

### Post by caoinan on 2007-08-27
its working now  thanks everyone I appreciate it

---

