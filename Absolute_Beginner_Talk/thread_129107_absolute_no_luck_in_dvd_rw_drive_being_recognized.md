---
title: "absolute no luck in dvd rw drive being recognized"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by garnertr on 2006-02-12
Greetings,

OK, linux dweeb here, cannot figure out WHY my dvdrw drive is not being regonized... any tips on where to start?

At this time I cannot play music, dvd's, data discs, nothing.. the drive simply dosen't seem to be recognized (the drive works find under windoze, suse and mandrivia)....

-----

tom@tardis:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0

-----

tom@tardis:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-9-386/volatile tmpfs rw,mode=0755 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0

-----

tom@tardis:~$ cd /media
tom@tardis:/media$ ls
cdrom  cdrom0  sda1
tom@tardis:/media$

-----

OK, I would like to know if I can FORCE Kubuntu to rescan my hardware and see if it can find my drive, is this possible?  I know I'm missing my drive out of my etc/fstab settings, but I'm not sure what "setting" it should be (hda, hdc, hdd, etc...)...

OK, any thoughts? thanks!!!!

---

### Post by Sutekh on 2006-02-12
[QUOTE=garnertr]I know I'm missing my drive out of my etc/fstab settings, but I'm not sure what "setting" it should be (hda, hdc, hdd, etc...)...

OK, any thoughts? thanks!!!![/QUOTE]
You can't hurt to try

Backup your fstab (makes it eaiser to scrub bad changes)
```

sudo cp /etc/fstab /etc/fstab_backup
```
Then edit it
```
sudo gedit /etc/fstab
```
And add this line for the DVD Drive
```
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

```
Then re-mount using
```
sudo mount -a
```
I only have one hard drive that is recognised as a **h**d# (SATA drives are  **s**d#), and my DVD drive is hdc.  If it doesn't work then try something else

---

### Post by garnertr on 2006-02-12
Well I tried each of my /media dir's /media/cdrom /media/cdrom0 and /media/sda1

sudo mount -a 

and ejected (manually) my cd and reinserted, drive powered up, and then shut down.. and again nothing changed...

any other thoughts??

-----

tom@tardis:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc /media/sda1 udf,iso9660 ro,user,noauto 0 0


currently listing in my etc/fstab... I've also removed HAL and reinstalled HAL, to no avail...

---

