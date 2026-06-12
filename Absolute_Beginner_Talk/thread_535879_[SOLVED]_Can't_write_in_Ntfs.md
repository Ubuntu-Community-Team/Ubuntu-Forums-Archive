---
title: "[SOLVED] Can't write in Ntfs?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-08-27
Hi all
I have ntfs mounted ..and ntfs 3g installed but I can't write in Ntfs file system . when I copy some thig and try to paste it in Ntfs partition I found that the paste option is not there in Ntfs dives// My fat drive is full so help me..How can I write in the folder that has lock icon and was established in Windows..

Plz help me :mad:

---

### Post by mikaelsnavy on 2007-08-27
have you tried writing to it as root? "sudo nautilus" in terminal?

---

### Post by wolfen69 on 2007-08-27
uninstalling ntfs-config and re-installing may fix it.

---

### Post by phyrewall on 2007-08-27
There's an installation of ntfs3g under automatix2 that basically takes care of it all for you, remounts all ntfs drives (and future mounts) in write mode.

---

### Post by aitorcalero on 2007-08-27
It seems that your ntfs partitions is in read only mode. Check it out in /etc/fstab file.

---

### Post by Dark Star on 2007-08-27
> **wolfen69 said:**
> uninstalling ntfs-config and re-installing may fix it.
```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=db33813a-44d9-420f-8a56-d50adc033e4c /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C4445B1A445B0F14 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=705E-3011  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=BCA0C683A0C6439C /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=a5d438cb-be42-4d3e-b5ad-ffce7e3ff115 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Btw I did not have NTFS config installed ?:?

---

### Post by Dark Star on 2007-08-27
Some body pl z help me I am running out of space :|

---

### Post by Hallvor on 2007-08-27
As mikaelsnavy said above, have you tried writing to it as root? 

Open up the terminal and type

```
sudo nautilus
```

Then try writing a file to it.

It *may* be a permission problem.

---

### Post by LowSky on 2007-08-27
uder system tools you should have an icon for ntfs cofiguration tool

make sure that "enable write support" is checked

---

### Post by klytu on 2007-08-27
> **Dark Star said:**
> ```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=db33813a-44d9-420f-8a56-d50adc033e4c /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C4445B1A445B0F14 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=705E-3011  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=BCA0C683A0C6439C /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=a5d438cb-be42-4d3e-b5ad-ffce7e3ff115 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Btw I did not have NTFS config installed ?:?

You will need NTFS config installed in order to enable write support. Try:

```
sudo aptitude install ntfs-config
```

---

### Post by Dark Star on 2007-08-27
```

Mounting /media/sda1 failed.

$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/disk/by-uuid/C4445B1A445B0F14': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

```
```

Mounting /media/sda6 failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/disk/by-uuid/BCA0C683A0C6439C': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

```

---

### Post by Dark Star on 2007-08-27
When I tick mark the options I got the above error and the NTFS driver get unmounted ;:(

---

### Post by Terl on 2007-08-27
Have you followed the instructions in the error message?

---

### Post by Dark Star on 2007-08-27
> **Terl said:**
> Have you followed the instructions in the error message?
Oops :o Never read that lemme do that :p

---

### Post by conjur3r on 2007-08-27
> **Dark Star said:**
> ```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=db33813a-44d9-420f-8a56-d50adc033e4c /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C4445B1A445B0F14 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=705E-3011  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=BCA0C683A0C6439C /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=a5d438cb-be42-4d3e-b5ad-ffce7e3ff115 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Btw I did not have NTFS config installed ?:?

You're going to need to safely unmount those drives first.  Then the most important step is to edit your /etc/fstab with the following:

```

UUID=C4445B1A445B0F14 /media/sda1     **ntfs-3g**    defaults,nls=utf8,umask=007,gid=46 0       1
UUID=BCA0C683A0C6439C /media/sda6     **ntfs-3g**    defaults,nls=utf8,umask=007,gid=46 0       1

```

Then unmount /media/sda1 and /media/sda6 and remount them (or just reboot).  You should now have write access.

---

### Post by kellemes on 2007-08-27
ntfs-config? Never used that.
Listen, if you install ntfs-3g you only have to edit your fstab by changing ntfs to ntfs-3g, and you should be done.

---

### Post by Dark Star on 2007-08-27
> **Terl said:**
> Have you followed the instructions in the error message?

Thanks for pointing out that :) working gr8 now :)

---

### Post by Terl on 2007-08-27
> **Dark Star said:**
> Thanks for pointing out that :) working gr8 now :)

No problem.  I get so frazzled sometimes myself and I overlook stuff.  Glad it is up and running.

---

