---
title: "where to mount second drive ???"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-11
I have a second drive installed and formatted.

================================================
squrl@squrl-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120000000000 bytes                                              <====
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System                                    
/dev/sdb1               1       14589   117186111   83  Linux                                  <====
squrl@squrl-desktop:~$ 
=============================================

What is the proper command to mount this drive so it shows up without having to go through /mnt

Also the line to add to /etc/fstab to bring it up at reboot automatically.


Thanks

---

### Post by Sqwishy on 2007-01-11
```

sudo mkdir /mnt/sdb
sudo mount /dev/sdb /mnt/sdb

```
i think?
i would put stuff in /media/ instead of /mnt/ but whatever

---

### Post by capitalistpiglet on 2007-01-11
Add this to the end of fstab
```
/dev/sdb1 /media/sdb1 	ext3    defaults        0       2
```
then run this command
```
sudo mount -a
```
to remount the drive, change /media/sdb1 to whatever you like but make sure the directory exists.

---

### Post by squrl on 2007-01-11
Thanks  for the help.....

---

### Post by squrl on 2007-01-11
Verrrryyyy frustrating. I doubt if either of those is the right answer. 
The first is wrong. It should refer to sdb1 not sdb
The second still leaves the directory or access to the drive buried in either /mnt or /media

---

### Post by taurus on 2007-01-11
What exactly do you plan to have /dev/sdb1 mounted to?

---

### Post by squrl on 2007-01-11
The goal was to have it stand alone like a usb drive does. Not be buried under some other /xxx where you have to dig to get to it. Maybe I'm not explaining this right but I think it should be possible to have it stand alone and not be dependent on another drive.

---

### Post by squrl on 2007-01-11
squrl@squrl-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G  2.2G  135G   2% /
varrun                506M   80K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  140K  9.9M   2% /proc/bus/usb
udev                   10M  140K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  488M   4% /lib/modules/2.6.17-10-386/volatile
/dev/sdb1             111G  189M  105G   1% /media/home2
/dev/sdc1              25G   16K   25G   1% /media/V1
/dev/sdc5              26G  3.4G   23G  14% /media/V2
/dev/sdc6              25G  1.5G   23G   6% /media/V3
squrl@squrl-desktop:~$ 


V1, V2, V3  all show up as separate drives. Your dont have to go through another layer to get to them.

In gnome commander they are free standing along side Home not buried in it

---

### Post by taurus on 2007-01-11
Mounting /dev/sdb1 to /media/sdb1 is similar to mounting /dev/sdc1 to /media/V1!  Maybe you need to reboot and there will be another icon on your desktop for /media/sdb1.

Is that what you mean by having an icon on your desktop for the drive?

---

### Post by squrl on 2007-01-11
I rebooted. When I go to the drop down (places) at the top of the screen it shows me 

Computer
CD/DVD
V1
V2
V3
(this is where I would like to see the second hard drive)

The V1, V2, V3 also show up as icons on the desktop. I dont have to go through home or computer to get to them.

---

### Post by taurus on 2007-01-11
What does your /etc/fstab look like again?

```
cat /etc/fstab
```

---

### Post by squrl on 2007-01-11
squrl@squrl-desktop:~$ sudo cat /etc/fstab
Password:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b34ea331-60f2-4351-8a61-6d50535b7cd7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b8f4fba9-4544-423b-9d04-7bb239811156 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
squrl@squrl-desktop:~$

---

### Post by taurus on 2007-01-11
Looks to me like you just unplugged your /dev/sdc drive!  

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   1
```
Save it and reboot.

Now, do you see an icon on your desktop for /media/sdb1?

---

### Post by squrl on 2007-01-11
Here is a new one.         I just usually use sudo gedit /etc/fstab  The gk bit seems to irritate the system.

squrl@squrl-desktop:~$ gksudo gedit /etc/fstab
(gedit:4677): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Ientered and rebooted but the drive is still buried.

---

