---
title: "Re: permissions for a slave harddrive - do not want to reformat"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by crushingbutterflies on 2007-07-11
I also have a slave hard drive, but I am not dual booting XP. I also do not want to reformat my hard drive if any way possible.

This is the contents of my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ccf4b16b-5087-406e-81b2-16b7fbcf9b5d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=bf9e78e4-426d-47c5-bed5-429a3bccd113 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by aysiu on 2007-07-11
I've made your support request into its own thread so it doesn't get lost in the shuffle or confuse people trying to help you.

Thanks for posting your /etc/fstab.

Can you also post the output of these two commands? Just copy and paste the commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then copy and paste the output back to this thread: ```
sudo fdisk -l
df -h
```

---

### Post by crushingbutterflies on 2007-07-15
Well, my slave drive is not even being recognized now. Good thing I copied all the files over to my main drive. I'm guessing there's a problem with the hard drive itself in addition to the formatting issues. Here's the stuff you asked for, but I don't think it will be of any use as the drive is not even being recognized:

```
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2341    18804051   83  Linux
/dev/sda2            2342        2434      747022+   5  Extended
/dev/sda5            2342        2434      746991   82  Linux swap / Solaris

Disk /dev/sdb: 5129 MB, 5129671680 bytes
255 heads, 63 sectors/track, 623 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         623     5004216   42  SFS
rachel@rachel-kelsey-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G   15G  2.2G  88% /
varrun                125M  100K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
procbususb            125M   88K  125M   1% /proc/bus/usb
udev                  125M   88K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   33M   92M  27% /lib/modules/2.6.20-16-generic/volatile

```

---

### Post by ReaderRat on 2007-07-15
If both the drives are on an IDE cable, do you have one set as Master and the other as Slave (on the actual hard drives)?

---

### Post by mad4dweb on 2007-08-29
SFS PROBLEM - SOLVED - NO NEED TO FORMAT THE DRIVE

1 - Check if your SFS drive is attached to the same IDE cable, place it on a separate cable
2 - Change the jumpers of the drive to SLAVE
3 - Open your NTFS-3g configuration
4 - Enable internal disk support
5 - You should have write permissions enable on the disk

I passed 2 weeks trying to make my NTFS hard drive work and followed several solutions posted like 
     - manually editing the /etc/fstab
     - installing NTFS-3g 

How ever they kept on faling and i could not make the drive become writable i came across with  this post  and decided to give it a try.

In my case i had the NTFS drive as slave  and attached to the same IDE cable, so the only thing a did was use a different Cable restarted the computer opened the NTFS-3g and now i can write to the drive. 

**sudo fdisk -l**
> Disco /dev/hdd: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdd1               1       30401   244196001   42  SFS


**cd /media | ls -la**
> drwxrwxrwx  1 root root 16384 2007-08-29 01:57 DATA-250

---

