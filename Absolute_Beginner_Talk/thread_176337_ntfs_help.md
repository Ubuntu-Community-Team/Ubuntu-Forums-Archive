---
title: "ntfs help"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by avidsensei on 2006-05-14
ok so im haveing a bit of trouble accessing my windows files (ntfs) i just want to listen to my music and watch my movies!
so heres what i tried to do



kyle@fast64:~$ /dev/sda1 2612 6527 31455270 7 HPFS/NTFS
bash: /dev/sda1: Permission denied
kyle@fast64:~$ sudo /dev/sda1 2612 6527 31455270 7 HPFS/NTFS
sudo: /dev/sda1: command not found
kyle@fast64:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
kyle@fast64:~$ sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9557    76766571   83  Linux
/dev/hda2            9558        9964     3269227+   5  Extended
/dev/hda5            9558        9964     3269196   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19452   156248158+   7  HPFS/NTFS
kyle@fast64:~$ /dev/sda1 2612 6527 31455270 7 HPFS/NTFS
bash: /dev/sda1: Permission denied
kyle@fast64:~$ cd /dev/sda1 2612 6527 31455270 7 HPFS/NTFS
bash: cd: /dev/sda1: Not a directory
kyle@fast64:~$
kyle@fast64:~$






it is on a serial ata disc so that is most likely my problem... assistance would be delightfull thanks

---

### Post by aysiu on 2006-05-14
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by avidsensei on 2006-05-14
yeah so that doesnt work because my 
sudo nano /etc/fstab
is blank.... what should i do now
also, should i simply replace hda1 with sda because im useing a serial ata hd?

---

### Post by aysiu on 2006-05-14
```
sudo nano /etc/fstab
``` can't turn up a blank document--otherwise, you wouldn't be able to use Ubuntu. Copy and paste the command I put here instead of retyping it.

And you should replace lines only if they refer to the same /dev. So /dev/sda1 should not replace /dev/hda1.

If there's no entry for /dev/sda1, add a new line.

---

### Post by avidsensei on 2006-05-14
allright so here is what i tried again


kyle@fast64:~$ sudo nano /etc/fstab
Password:
kyle@fast64:~$ sudo mount -a
[mntent]: line 1 in /etc/fstab is bad
mount: /dev/sda1 already mounted or /windows busy
mount: according to mtab, /dev/sda1 is mounted on /
kyle@fast64:~$ sudo umount /media/sda1
umount: /media/sda1: not found
kyle@fast64:~$ sudo umount /
umount: /: device is busy
umount: /: device is busy
umount: /: device is busy
kyle@fast64:~$ sudo umount /dev/sda1
umount: /: device is busy
umount: /: device is busy
kyle@fast64:~$  /
bash: /: is a directory
kyle@fast64:~$ kyle@fast64:~$ sudo umount /media/sda1
bash: kyle@fast64:~$: command not found
kyle@fast64:~$  /
bash: /: is a directory
kyle@fast64:~$ kyle@fast64:~$ sudo umount /media/sda1
bash: kyle@fast64:~$: command not found
kyle@fast64:~$ sudo umount /windows
umount: /windows: not mounted
kyle@fast64:~$ sudo umount /dev/sda1
umount: /: device is busy
umount: /: device is busy
kyle@fast64:~$ sudo nano /etc/fstab
kyle@fast64:~$ sudo mount -a
[mntent]: line 1 in /etc/fstab is bad
mount: /dev/sda1 already mounted or /windows busy
mount: according to mtab, /dev/sda1 is mounted on /
kyle@fast64:~$

---

### Post by cgjones on 2006-05-14
Try [this](http://help.ubuntu.com/starterguide/C/ch05.html) for more information. And post the contents of /etc/fstab here so we can see what the problem might be.

---

### Post by avidsensei on 2006-05-14
GNU nano 1.3.8             File: /etc/fstab

  /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /windows  ntfs    nls=utf8,umask=0222 0       0

---

### Post by aysiu on 2006-05-14
[QUOTE=avidsensei]GNU nano 1.3.8             File: /etc/fstab

  /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /windows  ntfs    nls=utf8,umask=0222 0       0[/QUOTE] Yes, line one is bad because it isn't commented out. It should be more like this: ```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /windows  ntfs    nls=utf8,umask=0222 0       0
``` It looks as if you might have accidentally deleted the # from the first line, which comments out the line.

---

### Post by avidsensei on 2006-05-14
kyle@fast64:~$ sudo nano /etc/fstab
kyle@fast64:~$ sudo mount -a
mount: /dev/sda1 already mounted or /windows busy
mount: according to mtab, /dev/sda1 is mounted on /
kyle@fast64:~$
kyle@fast64:~$ sudo umount /
umount: /: device is busy
umount: /: device is busy
umount: /: device is busy
kyle@fast64:~$ sudo umount /dev/sda1
umount: /: device is busy
umount: /: device is busy
kyle@fast64:~$




how do i get this to mount? or unmount it so i can remount it in the right spot?

---

### Post by aysiu on 2006-05-14
That's weird. /dev/hda1 is mounted at /
I don't see how /dev/sda1 could be mounted a / too.
Just reboot.

---

### Post by avidsensei on 2006-05-14
ok rebooted and hell yeah! thanks for helping guys!

---

### Post by avidsensei on 2006-05-14
hey another quick question, what is a good program to play your mp3's i liked winamp in windows, is there a linux version?
the ones that came with ubuntu are not playing my files, they see them but they dont play them

---

### Post by cgjones on 2006-05-14
To enable mp3 playback, read [this](http://help.ubuntu.com/starterguide/C/ch03.html#codecs)

---

### Post by avidsensei on 2006-05-14
is there an equivilant to ctrl alt delete? because vlc media player locked up and is not responding

---

### Post by sinkxdie on 2006-05-14
Umm, not really, can you open up Gnome's system guard or whatever its called and kill the process?

---

### Post by avidsensei on 2006-05-14
how do you open that up? or where is it?

---

### Post by catlett on 2006-05-14
You should be able to use the System Monitor like the Task Manager (I don't know because where I used it 5 times a day on windows I never used it in linux) But it appears to be the same thing. You can see what processes are running and you can "end process". It should work like task manager.
Go to the top of the screen and hit on "Applications" when the menu drops down scroll to "system tools" When that menu opens up scroll to "system monitor"

---

