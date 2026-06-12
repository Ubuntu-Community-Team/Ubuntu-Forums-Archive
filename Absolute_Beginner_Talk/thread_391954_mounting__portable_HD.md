---
title: "mounting  portable HD"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2007-03-23
Sorry I thought is was solved , on rebooting the next morning the portable usb wouldnt mount I ve tried
$ chmod 777 /media/eportable

followed the wiki on changing the fstab
for both files and volumes

followed the above web page for mounting extra HD

and nothing

I can mount it by $ mount -a ( in root )

but I cant get it to mount in my home  ( user..ie change permission for non root user to mount it ) 

tried Kuser but it couldnt open psswrd.bak to save changes ...\

( it works fine with windows xp and ubuntu 6.10 on laptop .....

I tried reformating it as ex3 , with no luck ...


Lost for Ideas ,,anyone ??????

Stephen


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sda1 /media/eportable ext3 defaults 0 0

---

### Post by taurus on 2007-03-23
If it is ext3 and already mounted to /media/eportable, then just change the ownership from root to your login name, assuming it's **stephen**.

```
sudo chown -R **stephen**:**stephen** /media/eportable
sudo chmod -R 755 /media/eportable
ls -la /media
```

---

### Post by basilwatson on 2007-03-24
Thanks Taurus 

I tried what you suggested and It still wont mount 

mount: only root can mount /dev/sda1 on /media/eportable

is the error message I get back ..

If I go into terminal and type mount  -a  ( in root ,,it will mount ok ) 

but I have tried updating , ftab as per wiki and  still no Joy 

any Ideas 

Stephen

---

### Post by taurus on 2007-03-24
Can you post the outputs of these commands from a terminal.

```
sudo fdisk -l
df -h
```

---

### Post by basilwatson on 2007-03-24
> **taurus said:**
> Can you post the outputs of these commands from a terminal.

```
sudo fdisk -l
df -h
```

sure 

s@s-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1284    10313698+   7  HPFS/NTFS
/dev/hda2            1285        9729    67834462+  83  Linux

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4870    39118243+  83  Linux
s@s-desktop:~$

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4870    39118243+  83  Linux
s@s-desktop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hda2              64G   50G   11G  83% /
varrun                379M   84K  379M   1% /var/run
varlock               379M  4.0K  379M   1% /var/lock
udev                  379M  128K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   19M  361M   5% /lib/modules/2.6.15-28-386/volatile
/dev/hda1             9.9G  5.5G  4.5G  56% /media/hda1
s@s-desktop:~$


also 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1      /media/eportable ext3 defaults 0 0


this is after a reboot and NOT logged in as root ...user ..s    

thanks for taking the time with this much apprieciated 

Stephen

---

