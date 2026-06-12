---
title: "U3 1G USB drive"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by wademunkey on 2007-08-16
I have  a 1G U3 thumb drive that I am trying to get working to transfer data to and from my laptop to the computers at school.  I am running Linux 7.04 Feisty Fawn.  Whenever I try to load a  document onto this device it tells me that the file I am trying to create does not exist.  Is there something within the software of the device that is leading into these issues?  I can see the icon for the device on my desktop, so it is mounted?  I can look at the files on the device, but they cannot be deleted, they are for the Windows users auto run and such.  There is a windows program to get rid of this programing, but I am not around a windows computer at all.  I am hoping to be able to figure this out, but I can get to a windows computer if it is absolutely necessary.  I am not able to create folders, or save files to the device, it tells me that the file name does not exist.  Any help would be greatly appreciated, and tell me if any of this is confusing, i know it is winded.
Andrew

---

### Post by wademunkey on 2007-08-16
I forgot to mention, I am unable to see the device in the Gnome partition editor as well.

---

### Post by blithen on 2007-08-16
I haven't had much problems with this but maybe I can help
Can you type in
```
mount
```
in the terminal and post what comes up?
Also what version of ubuntu?

---

### Post by mc4man on 2007-08-16
if you want to remove the u3 feature (partition) there's an uninstall - u3 uninstall.exe (only works from windows i believe) but having/keeping it shouldn't prevent you from reading and writing to like any other usb drive. I've got 2 mounted right now, 1 with u3, 1 with u3 removed both work fine. As far as gparted are you clicking down the box at top right to show add. drives?  What brand?

---

### Post by wademunkey on 2007-08-17
Alright, sorry about not responding quicker, had a problem finding my post.  I am using a  PNY attache 1G running the U3 smart technology.   My computer is a dell Inspiron 600m running only Ubuntu Feisty Fawn I believe it is V. 7.04.
When I type in mount in the terminal this comes up
wademunkey@wademunkey-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/scd1 on /media/sdc type iso9660 (ro,nosuid,nodev,uid=1000,utf8)
 The last line is being weird and putting  a smilie in, so here is what the end says spaced out , u i d = 1 0 0 0 , u t f 8 )
I am runnign two hardrives,a dn i can see both of them, but I cannot see my thumb drive.  when i look at the properties of the thumb drive it tells me that  the file system is ISO9660(joliet extension) ANd it tells me that mount point is /media/sdc. 
When I look at the gnome partition editor, My main hard drive sda is shown, and my external sdb is shown.  there is no other drive, and I know that it is connected.  
I hope this is all the information you all need. thanks for the help
Andrew

---

### Post by sourjax on 2007-08-17
You should be able to delete to U3 files by:

```

sudo umount /media/sdb1

sudo umount /media/scd1

sudo mount -o rw /media/sdb1

sudo rm -R /media/sdb1/*

```


But as far as your other problems I'm at a loss because I have no problems writing to my 2G U3 Sandisk, it may be that you have a bad USB or something, but pls don't give up.

---

### Post by wademunkey on 2007-08-19
nobody else has any ideas??

---

### Post by wademunkey on 2007-08-20
I have figured it out.  I uninstaller the U3 software through a windows based machine.  The file system if the drive switched to fat16.  I can see the thumb drive in the gnome partition editor.  I can save to the drive, and I can see the files on the drive.  It appears to me that the drive was using a different file system.  It was like iso (some number).  Thanks for everyone's help.
Andrew

---

### Post by MQMike on 2007-08-20
U3, remove it from UFD:  [www.U3.com/uninstall](www.U3.com/uninstall)
(from Windows)

---

