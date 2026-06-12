---
title: "help...just made separate/home"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by natehatewindows on 2007-11-15
i just made a separate /home and now all of my settings went back to how they were when i did a new install....what happened? i lost everything in settings, bookmarks, my kopete stuff....how do i tell if this really worked? im lost....

---

### Post by taurus on 2007-11-15
Did you copy all your settings from old /home to the new /home before you mount it?  Or did you just create a new /home and mount that new partition to /home in /etc/fstab?

---

### Post by ByteJuggler on 2007-11-15
It's not clear what you did.  Did you just format your entire hard drive and reinstall, creating a new seperate home partition?  Or did you make another install alongside your old one (with a seperate /home)?

---

### Post by natehatewindows on 2007-11-15
i did what was listed here [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

i just did the partitioning different

its making me install all the updates and stuff again too :( but seems to work ok.

---

### Post by natehatewindows on 2007-11-15
is there anyway to tell if im really using the new /home partition?

should there still be a folder in my computer called home and home_backup

i made the home_backup when i did this so i know it should be there...but what about the other home folder? is it still in use? how do i tell? thanks! :)

---

### Post by taurus on 2007-11-15
Post the outputs of these commands from a terminal?

```
cat /etc/fstab
df -h
```

---

### Post by natehatewindows on 2007-11-15
home@home-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=27c96fda-9808-4018-a7cf-737a53434618 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=BC0816BF0816791A /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=e0c6a6ab-e798-4e88-91ae-798adb4556f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1       /home    ext3     nodev,nosuid  0  2
home@home-laptop:~$ 

home@home-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              22G  4.1G   17G  20% /
varrun               1009M  112K 1009M   1% /var/run
varlock              1009M  4.0K 1009M   1% /var/lock
udev                 1009M   80K 1009M   1% /dev
devshm               1009M     0 1009M   0% /dev/shm
lrm                  1009M   34M  976M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              20G  1.3G   18G   7% /home
home@home-laptop:~$

---

### Post by natehatewindows on 2007-11-15
looking at this i see another issue...

sda2 is no longer on my computer because i deleted windows and thats where it was

should i remove it from fstab?

---

### Post by taurus on 2007-11-15
> **natehatewindows said:**
> home@home-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=27c96fda-9808-4018-a7cf-737a53434618 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=BC0816BF0816791A /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=e0c6a6ab-e798-4e88-91ae-798adb4556f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1       /home    ext3     **[COLOR="Blue"]nodev,nosuid[/COLOR]**  0  2
home@home-laptop:~$ 


Why wouldn't you make that line to look like

```
/dev/sda1     /home     ext3     defaults     0     1
```
Can you boot your machine with a LiveCD?

p.s.  Can you post

```
sudo fdisk -l
```

---

### Post by natehatewindows on 2007-11-15
thats just what the instructions said to do....yes i can...

what should i do after i boot?

---

### Post by taurus on 2007-11-15
Boot from the LiveCD and post post the output of this command.  Will see if your original settings are still in the old /home.

```
sudo fdisk -l
```

---

### Post by natehatewindows on 2007-11-15
[sudo] password for home:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeef6b203

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            8797       11407    20972857+  83  Linux
/dev/sda3           11408       11686     2241067+  82  Linux swap / Solaris
/dev/sda4           11687       14593    23350477+  83  Linux
home@home-laptop:~$

---

### Post by natehatewindows on 2007-11-15
ok well i dont have internet with live disk because i have a winmodem.

i dont really care if i have to redo my settings, most i already did just now but i want to maek sure this new /home is working right so i delete the home_backup

---

### Post by taurus on 2007-11-15
> **natehatewindows said:**
> [sudo] password for home:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeef6b203

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            8797       11407    20972857+  83  Linux
/dev/sda3           11408       11686     2241067+  82  Linux swap / Solaris
/dev/sda4           11687       14593    23350477+  83  Linux
home@home-laptop:~$

You need to mount / and remove the entry for /dev/sda2 since there is no /dev/sda2 anymore.

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda4 /media/ubuntu
gksudo gedit /media/ubuntu/etc/fstab
```

Now, your old $HOME directory should be in /media/ubuntu/home/**username**.  At the same time, you can mount your new /home partition, /dev/sda1, some somewhere else so you can copy stuff over.

```
sudo mkdir /media/new_home
sudo mount -t ext3 /dev/sda1 /media/new_home
```

---

### Post by natehatewindows on 2007-11-15
so i shoudl do this from the live cd? i dont understand....it looks like im making a backup of my old /home. i already have a backup. im confused sorry

---

### Post by natehatewindows on 2007-11-15
gparted says my new /home partition is mounted but i cant find it under computer

---

### Post by natehatewindows on 2007-11-15
maybe im just donfusing myself...i dont know. if i got to computer>>file system i see a home folder. if i right-click properies it says Location:/ volume: /home

i see a home_backup folder too. location:/ volume:/

what is this? is my new home partion working right? im sorry for being stupid but i just dont know how to tell.

---

### Post by natehatewindows on 2007-11-15
> **taurus said:**
> Why wouldn't you make that line to look like

```
/dev/sda1     /home     ext3     defaults     0     1
```
Can you boot your machine with a LiveCD?

p.s.  Can you post

```
sudo fdisk -l
```

ok, im pretty sure my /home partition is working because if it was not i dont see why my setting would change. so can i just do ```
sudo gedit /etc/fstab
``` to delete the sda2 lines and change the nodev,nosuid to defaults? 

should my / not be mounted now that i have a new /home partition? because it is mounted according to gparted

---

