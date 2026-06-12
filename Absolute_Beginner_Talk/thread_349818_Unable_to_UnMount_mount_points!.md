---
title: "Unable to UnMount mount points!"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by marx2k on 2007-01-30
I've been having some issues with my NFS, but I think I have it solved (FOR THE MOST PART)..

Anyway, here's my FSTAB...

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
/dev/sda1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
/dev/hda1 /media/hda1     ext3    defaults        0       2
# /dev/hdb1
/dev/hdb1 /media/hdb1     ext3    defaults 0 2
# /dev/sda2
UUID=436826df-92fa-4066-903a-b32e7a9be817 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

#SAMBA Shares
#//192.168.11.8/MyMusic1 /home/marx2k/SambaShares/Music/Collection1   cifs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
#//192.168.11.8/MyMusic2 /home/marx2k/SambaShares/Music/Collection2   cifs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
#//192.168.11.8/MyMusic3 /home/marx2k/SambaShares/Music/Collection3   cifs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
#//192.168.11.8/MyMusic4 /home/marx2k/SambaShares/Music/Collection4   cifs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
#//192.168.11.8/MyDocuments /home/marx2k/SambaShares/Documents   cifs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
#//192.168.11.8/MyPictures /home/marx2k/SambaShares/Pictures   cifs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
#//192.168.11.8/shared /home/marx2k/SambaShares/ReadWrite   cifs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0

#rw,rsize=32768,wsize=32768,hard,intr,nfsvers=3,tcp,noatime,nodev,async,lock

#NFS Mounting - rsize=8192,wsize=8192,timeo=14,intr
192.168.1.101:/media/hdb4/Music /home/marx2k/Desktop/LivingroomBuntu/Music/Collection1 nfs rw,rsize=8192,wsize=8192,soft,nodev,async,lock 
192.168.1.101:/media/hdd3/Music /home/marx2k/Desktop/LivingroomBuntu/Music/Collection2 nfs rw,rsize=8192,wsize=8192,soft,nodev,async,lock
192.168.1.101:/media/hdf2/Music /home/marx2k/Desktop/LivingroomBuntu/Music/Collection3 nfs rw,rsize=8192,wsize=8192,soft,nodev,async,lock
192.168.1.101:/media/hde3/Music /home/marx2k/Desktop/LivingroomBuntu/Music/Collection4 nfs rw,rsize=8192,wsize=8192,soft,nodev,async,lock
192.168.1.101:/media/hdf3/DOCS  /home/marx2k/Desktop/LivingroomBuntu/Documents nfs rw,rsize=8192,wsize=8192,soft,nodev,async,lock
192.168.1.101:/media/hde2/Shared  /home/marx2k/Desktop/LivingroomBuntu/Scratch nfs rw,rsize=8192,wsize=8192,soft,nodev,async,lock

```

However, when I try 'sudo umount -a', I get:
```

umount: /home/marx2k/Desktop/LivingroomBuntu/Scratch: device is busy
umount: /dev: device is busy
umount: /proc/bus/usb: device is busy
umount: /var/run: device is busy
umount: /sys: device is busy
umount: /: device is busy

```

I am unable to unmount that NFS share! 

This doesnt work either:
```

marx2k@Commodore-64:~$ sudo umount -f  /home/marx2k/Desktop/LivingroomBuntu/Scratch
umount2: Device or resource busy
umount: /home/marx2k/Desktop/LivingroomBuntu/Scratch: device is busy
umount2: Device or resource busy
umount: /home/marx2k/Desktop/LivingroomBuntu/Scratch: device is busy

```

Nothing is using it:
```

marx2k@Commodore-64:/etc/init.d$ lsof | grep /home/marx2k/Desktop/LivingroomBuntu/Scratch
marx2k@Commodore-64:/etc/init.d$ lsof | grep Scratch
marx2k@Commodore-64:/etc/init.d$
marx2k@Commodore-64:~$ fuser -m /home/marx2k/Desktop/LivingroomBuntu/Scratch
marx2k@Commodore-64:~$ 

```

---

### Post by marx2k on 2007-01-30
figured out what was doing it... 

```

marx2k@Commodore-64:~$ sudo fuser -m /home/marx2k/Desktop/LivingroomBuntu/Scratch
/home/marx2k/Desktop/LivingroomBuntu/Scratch:  5000

```

And that was...
marx2k    5000  0.0  0.1   3012  1104 ?        Ss   17:36   0:00 /usr/sbin/famd -T 0

Killed that and the system allowed me to finally unmount that directory.

GRRRRR

---

