---
title: "Fstab Help Hidden Mistake"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by banditv1 on 2007-04-24
Below is a copy of my fstab file. I must have made a mistake, but I can't find it.
Perhaps I am looking through the trees to see the woods ( pun )

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f5219a5b-5c82-4f37-a7c7-170875b92045 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6381630e-a55f-4272-8c14-d6199c605f69 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1 /mnt/hdb1 auto defaults,user 0 0
/dev/hdd1 /mnt/hdd1 auto defaults,user 0 0

I did create two directories for these in the /mnt.
if I was to cd to the hdb1 directory the pwd should show mike@homeftp:/mnt/hdb1$  Right?

Now I would like for the person going "OH OH I know" to kindly post the answer to the dumb mistake I have made.

---

### Post by banditv1 on 2007-04-24
An easy little bump here.  HEY you there...Yeah you I see your Super Ubuntu User Shirt. :lol:  I got a question for you... I will be right back....

---

### Post by aysiu on 2007-04-24
What's the problem exactly?

---

### Post by guysmiley25 on 2007-04-24
Yes what error are you getting?

Looking at your fstab it looks like this is the stuff you added.
```

/dev/hdb1 /mnt/hdb1 auto defaults,user 0 0
/dev/hdd1 /mnt/hdd1 auto defaults,user 0 0

```

Maybe you need to specify the file system. eg
```

/dev/hdb1 /mnt/hdb1 ext3 defaults,user 0 0
/dev/hdd1 /mnt/hdd1 ext3 defaults,user 0 0

```

---

### Post by banditv1 on 2007-04-24
Oh very sorry for that but the drive do not show up in computer.

---

### Post by aysiu on 2007-04-25
> **banditv1 said:**
> Oh very sorry for that but the drive do not show up in computer.
Can you post the output of these commands? ```
cd /mnt/hdb1
ls
```

---

### Post by nanotube on 2007-04-25
and post the output of command
```
mount
```

that should show all mounted drives.

---

### Post by banditv1 on 2007-04-25
Here is the information you requested. 
mike@homeftp:/mnt/hdb1$ ls
mike@homeftp:/mnt/hdb1$

mike@homeftp:/mnt/hdb1$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
mike@homeftp:/mnt/hdb1$

---

### Post by nanotube on 2007-04-25
ok, so mount clearly shows that those drives are not mounted. so now the question is, why is that. :) 
run command
```
sudo fdisk -l
```
that will list all the physical disks/partitions you have, and we will go from there. 

edit: (by the way, that -l is the letter L, not number 1, just to be clear. )

---

### Post by banditv1 on 2007-04-25
Here is the information you requested.
Is it because the drives are formatted as fat32, why they are not working?
If I am not mistaken Linux systems can read and right to fat32.  If not is there utility I can use to format them to ext3. Dose 7.04 have an fdisk utility for managing newly installed drives?

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9964    80035798+   b  W95 FAT32

Disk /dev/hdd: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        7301    58645251    b  W95 FAT32

---

### Post by aysiu on 2007-04-25
Can you paste these commands (in this order) into the terminal and then paste back here the output of all the commands? ```
sudo mkdir /media/hdd1
sudo mount /dev/hdd1 /media/hdd1 -t vfat -o iocharset=utf8,umask=000
df -h
cd /media/hdd1
ls
```

---

### Post by banditv1 on 2007-04-25
Here is the information that you requested.
This makes me think that Ubuntu dose not like the formatting of the drives. 
Looks like I may have to reformat them using the ext3 file system. :-k Not sure if that will cause me any issues later but looks like I may not have a choice.

mike@homeftp:/media$ sudo mkdir /media/hdd1
mike@homeftp:/media$

mike@homeftp:/media$ ls
cdrom  cdrom0  floppy  floppy0  hdd1
mike@homeftp:/media$ 

mike@homeftp:/media$ ls
cdrom  cdrom0  floppy  floppy0  hdd1
mike@homeftp:/media$ sudo mount /dev/hdd1 /media/hdd1 -t vfat -o iocharset=utf8,umask=000
mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mike@homeftp:/media$ dmesg | tail 
[   35.120000] Bluetooth: HCI socket layer initialized
[   35.180000] Bluetooth: L2CAP ver 2.8
[   35.180000] Bluetooth: L2CAP socket layer initialized
[   36.276000] Bluetooth: RFCOMM socket layer initialized
[   36.276000] Bluetooth: RFCOMM TTY layer initialized
[   36.276000] Bluetooth: RFCOMM ver 1.8
[   49.768000] eth0: no IPv6 routers present
[12567.000000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[12567.000000] FAT: bogus number of reserved sectors
[12567.000000] VFS: Can't find a valid FAT filesystem on dev hdd1.
mike@homeftp:/media$

---

### Post by aysiu on 2007-04-25
Okay. Something's wrong. ```
sudo fdisk -l
``` says /dev/hdd1 is FAT32, but ```
dmesg | tail
``` says it's not...

---

### Post by banditv1 on 2007-04-25
That is what I thought too. I have no idea what caused this issue. The only thing I can think of now is to reformat the hard drives. Is there a utility in Ubuntu That will allow me to do this with out having to redo the entire system; or taking the whole rack mount box down and apart again.#-o 

By the way thanks to every one for all your help and brain power.

---

### Post by aysiu on 2007-04-25
I've never done this before, but you may find GPart helpful. More details in here:
[HOWTO: Restore Lost Partitions to a Deleted or Corrupt Partition Table](http://ubuntuforums.org/showthread.php?t=370121)

---

### Post by banditv1 on 2007-04-25
Thanks for that idea, but I am not far into system setup so I think I will just reinstall every thing new. Besides its not like it is hard to install Ubuntu. Seven easy steps to bliss:lolflag: . 
Thanks again to every one who tried to help.

---

### Post by banditv1 on 2007-04-25
I am running on the live cd now. Just to make sure I am right here, have I set this up right?
If not please post a corrections. Then let me know how to set up the mount points for the extra drives.

---

### Post by nanotube on 2007-04-25
> **banditv1 said:**
> I am running on the live cd now. Just to make sure I am right here, have I set this up right?
If not please post a corrections. Then let me know how to set up the mount points for the extra drives.

before you go and reformat everything, why not try running fsck on the disks, and see if you can correct the problem?

try
```
sudo fsck.vfat -r /dev/hdd1
```
and see if that catches any errors, and it does, then try mounting it again with "mount" as you did above.

but of course, if you are just going to use those disks for storage, ext3 is a better filesystem, so you are better off reformatting to ext3 
but just out of curiosity, try the fsck. ;)

---

### Post by ububaba on 2007-04-26
[HTML]:~$ sudo mount -a
[mntent]: line 12 in /etc/fstab is bad
[/HTML]
[COLOR="Blue"]
What is meant line 12 being bad? How can it be impoved? The fstab contents are shown below. 
[/COLOR]
[HTML]ubu@baba:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=009f8eda-4bb9-4db4-8681-eb282ad26caf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=e0b9dd48-229d-45b2-9edb-72f37e8b8d5c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

/dev/sda3       /media/sda3     /home           ext3    defaults        0       1
[/HTML]

---

### Post by aysiu on 2007-04-26
Maybe it's the line that says ```
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

``` Notice how there's nothing after *dev/*?

---

### Post by igknighted on 2007-04-26
my money is on the last line.  You have two mount points listed there (/media/sda3 and /home)

---

### Post by ububaba on 2007-04-26
> **igknighted said:**
> my money is on the last line.  You have two mount points listed there (/media/sda3 and /home)

Thanks. You do put your money where your mouth is.:guitar:

---

