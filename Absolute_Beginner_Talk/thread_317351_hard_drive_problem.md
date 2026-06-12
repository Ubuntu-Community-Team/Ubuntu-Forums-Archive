---
title: "hard drive problem"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by mixmaster87 on 2006-12-12
today, i added 2 ekstra hard drives to my comp (ide disks i used to fill in every kind of stuff in, but when i try to go into any of these hard drives this message comes up:

error: device /dev/hdd1 is not removable

error: could not execute pmount


both are 120gb, no partitions, filled with .mp3, .avi, and other windows junk i used before:P what should i do to enable those drives?

---

### Post by bodhi.zazen on 2006-12-12
> **mixmaster87 said:**
> today, i added 2 ekstra hard drives to my comp (ide disks i used to fill in every kind of stuff in, but when i try to go into any of these hard drives this message comes up:

error: device /dev/hdd1 is not removable

error: could not execute pmount


both are 120gb, no partitions, filled with .mp3, .avi, and other windows junk i used before:P what should i do to enable those drives?

You need to mount them.

See here:

Overview: make a mount point, mount, edit fstab.

Mounting and permissions depends on the file system:

_Windows:_

For read-write: [Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
[list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and umask=000[/list]

_Linux_: [Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)

To mount at boot you will need to edit /etc/fstab (as outlined in the links above). For an overview of fstab see:
[How to fstab]()
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

See also [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by deadgobby on 2006-12-12
All so 
[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by mixmaster87 on 2006-12-12
i have come so far that i have done everything in that guide, exept doing ```
sudo chown -R marie:marie /storage
``` (marie as it was the username used in the example, changed it to mixmaster).

now i got a directory named storage, but i got no permission to go into the directory.

"You do not have the permissions necessary to view the contents of "storage"."

how do i run that sudo chown -R marie:marie /storage code? what to fill in instead of "marie:marie"?

EDIT: btw, those drives where ntfs if that counts.

---

### Post by deadgobby on 2006-12-12
MMM are you working with western digital HD's?

---

### Post by mixmaster87 on 2006-12-12
yepp

---

### Post by deadgobby on 2006-12-12
Ok Let me reboot my system. Because you may need to lie to your BIOS. Because when I changed my boot up selection. Even though the you may set up the BIOS at master and slave. The two see each other, but will not mount. Please stand by. Please listen to some music!

---

### Post by mixmaster87 on 2006-12-12
my music is in one of those drives:P anyway, thx for helping out then!

what should i do with the list i used to mount those drives then? delete it and rename the backup file to the original?

---

### Post by deadgobby on 2006-12-12
OK if you have Award Software as your standard CMOS. Here is what you can check. Go into BIOS. Once into BIOS goto Advance BIOS Features. 
Go down to the 3rd  Boot Device
Check to see if HDD-2 is selected. 
You may need to play with it for the master HD to boot up. I been there really I have. I have 2 WD HD's and had to play with the BIOS before I can mount the 2CD HD. The new 120 gig as master and 40 gig as slave. When I was able to to get that going. I got the 2cd HD to read. After reboot I could not see it. So I posted on that
[http://ubuntuforums.org/showthread.php?t=294228](http://ubuntuforums.org/showthread.php?t=294228)

---

### Post by mixmaster87 on 2006-12-12
as i installed linux and used it for the wery first time on sunday, that was abit too mutch information at one time (thou i know bios is not linux only, i just dont know mutch about bios:P)

this is what fdisk gives me right now

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9331    74951226   83  Linux
/dev/sda2            9332        9729     3196935    5  Extended
/dev/sda5            9332        9729     3196903+  82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       14593   117218241    7  HPFS/NTFS

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       14593   117218241    7  HPFS/NTFS

---

### Post by deadgobby on 2006-12-12
> **mixmaster87 said:**
> as i installed linux and used it for the wery first time on sunday, that was abit too mutch information at one time (thou i know bios is not linux only, i just dont know mutch about bios:P)

this is what fdisk gives me right now

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9331    74951226   83  Linux
/dev/sda2            9332        9729     3196935    5  Extended
/dev/sda5            9332        9729     3196903+  82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       14593   117218241    7  HPFS/NTFS

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       14593   117218241    7  HPFS/NTFS
 Mine would read the same. Go into BIOS and see if the post I gave you works.
Gobby

---

### Post by mixmaster87 on 2006-12-12
at least, if i try to use that command i failed at, i get this:

mixmaster@prodigy:~$ sudo chmod -R mixmaster:mixmaster /storage
chmod: invalid mode: `mixmaster:mixmaster'
Try `chmod --help' for more information.

and i dont know what award software or cmos is:P

---

### Post by dmartinsca on 2006-12-12
The command should be **sudo chown -R mixmaster:mixmaster /storage**

Also, I don't think you need to change anything in your BIOS since it looks like both 120GB drives are seen as /dev/hdc and /dev/hdd. As long as those are the  drives you installed, that's good. The problem seems to be with file permissions, which should be easy enough to fix.

I assume you have mounted a drive on /storage? What is the output of **ls -ld /storage**
What does your /etc/fstab look like now?
Oh, also the output from **mount**

---

### Post by deadgobby on 2006-12-12
> **dmartinsca said:**
> I don't think you need to change anything in your BIOS since it looks like both 120GB drives are seen as /dev/hdc and /dev/hdd. As long as those are the  drives you installed, that's good. The problem seems to be with file permissions, which should be easy enough to fix.

I assume you have mounted a drive on /storage? What is the output of **ls -ld /storage**
What does your /etc/fstab look like now?
OK have you taken 2 WD HD's and try to mount them? 
Gobby

---

### Post by mixmaster87 on 2006-12-12
how do i get ls -ld /storage?

Edit: found out:P

mixmaster@prodigy:~$ ls -ld /storage
dr-x------ 1 root root 12288 2006-12-09 18:31 /storage

mixmaster@prodigy:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/hdd1 on /storage type ntfs (rw)
/dev/hdc1 on /storage type ntfs (rw)

and they are both in storage now, i presume

---

### Post by deadgobby on 2006-12-12
simple just go to Applications> Accessories> Terminal
Copy and paste the commands above. You will still need to edit your BIOS for the slave to be read. You'll see.
Gobby
Off to bed I go from working 3rd shift.

---

### Post by mixmaster87 on 2006-12-12
i dont like playing with bios...:( its scary:P

---

### Post by dmartinsca on 2006-12-12
deadgobby, both drives are already mounted!

mixmaster, you can't mount both drives to the same place. What happens is only the contents of the second drive mounted will be visible at /storage. You'll need to make a second directory to mount one of the drives on and change your /etc/fstab file accordingly.

The permission problem seems to be due to your mount options in /etc/fstab. Could you post the contents of that file after making the changes to the mount point?

---

### Post by mixmaster87 on 2006-12-12
i tried to change things but when i got to "sudo mount -a" i got```
mixmaster@prodigy:~$ sudo mount -a
mount: /dev/hdd1 already mounted or /windows busy
mount: according to mtab, /dev/hdd1 is mounted on /storage

```

oh, gotta unmount it first mabye?:P back in a minute:P

---

### Post by mixmaster87 on 2006-12-12
you mean this?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd1       /windows        ntfs    defaults         0      0
/dev/hdc1       /storage        ntfs    defaults         0      0

---

### Post by dmartinsca on 2006-12-12
yes, you'll need to unmount /dev/hdd1 first before remounting it on a different location.

Also, change the following lines in /etc/fstab
```

/dev/hdd1 /windows ntfs defaults 0 0
/dev/hdc1 /storage ntfs defaults 0 0
```
to
```
/dev/hdd1 /windows ntfs defaults,umask=000 0 0
/dev/hdc1 /storage ntfs defaults,umask=000 0 0
```

After saving the file you'll need to remount both drives. This should hopefully fix your permission denied problem.

One more thing, the ntfs driver you're using only allows you to read from the drives. If you need to write to them, you'll need to install the ntfs-3g driver and change the part in your fstab file from ntfs to ntfs-3g. There was a link to a guide on the first page of this thread which should help you along.

---

### Post by mixmaster87 on 2006-12-12
yay, it worked:D but, am i able to change the name of the directory with just nameswitching it? or do i have to use those terminal commands again and change it there?

really thanks for this:D

---

### Post by dmartinsca on 2006-12-12
You'll have to create the new directory, edit /etc/fstab to point to the new directory, unmount the drive and remount it.

Glad i could help. Welcome to linux! Don't worry, things get a lot easier once you develop an understanding of the system. :)

---

### Post by mixmaster87 on 2006-12-12
i understand alot already, figured out how to install and set up beryl xgl with a guide here in the forums, and with it i understood how apt-get and stuff worked:D im a fast learner:P thanks:p

---

