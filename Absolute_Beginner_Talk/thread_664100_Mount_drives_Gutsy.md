---
title: "Mount drives Gutsy"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by spookyct on 2008-01-10
I'm currently running Gutsy and my NTFS drive is not show under /media/hdb1

This drive has all of my media on it...  can anyone help!?

:confused::confused::confused::confused::confused:

---

### Post by vikram on 2008-01-10
can you post the output of the following commands it will help determine if the problem is with mounting

sudo fdisk -l 

mount

cat /etc/fstab

---

### Post by spookyct on 2008-01-10
> **vikram said:**
> can you post the output of the following commands it will help determine if the problem is with mounting

sudo fdisk -l 

mount

cat /etc/fstab

```
james@james-desktop:/media/hdb1$ sudo fdisk -l
[sudo] password for james:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1371d154

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066e73

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6079    48829536   83  Linux
/dev/sdb2            6080        6203      996030   82  Linux swap / Solaris
james@james-desktop:/media/hdb1$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-386/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
james@james-desktop:/media/hdb1$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=db329ffa-9372-481d-a264-440e8a0955be /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=68D4807DD4804F6E /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=f372f85f-e8fc-4c3c-82ae-f8fb02397f90 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
james@james-desktop:/media/hdb1$ 

```

---

### Post by vikram on 2008-01-10
not a linux expert but I dont think the disk is mounted.

get the uuid of the disk /dev/hdb1 like so

```

sudo /sbin/vol_id -u /dev/hdb1

```see  link for details
[https://help.ubuntu.com/community/UsingUUID?highlight=%28uuid%29](https://help.ubuntu.com/community/UsingUUID?highlight=%28uuid%29)

is this the same as your uuid in the /etc/fstab file ?

# /dev/hdb1
UUID=68D4807DD4804F6E /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

if not you need to change it to the correct uuid.

alternatively try manually mounting it for errors, sometimes if you dont shutdown windows cleanly the device wont mount. if you have windows, restart in windows and shutdown cleanly before trying again.

```

sudo **mount** -t ntfs /dev/hdb1 /media/hdb1

```more help for mounting
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=mount&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=mount&titlesearch=Titles)

hope this helps

---

### Post by spookyct on 2008-01-10
```
james@james-desktop:/media/hdb1$ sudo mount -t ntfs /dev/hdb1 /media/hdb1
[sudo] password for james:
Failed to access '/dev/hdb1': No such file or directory
james@james-desktop:/media/hdb1$ sudo /sbin/vol_id -u /dev/hdb1
/dev/hdb1: error opening volume
james@james-desktop:/media/hdb1$ sudo mount -t ntfs /dev/hdb1 /media/hdb1
Failed to access '/dev/hdb1': No such file or directory
james@james-desktop:/media/hdb1$ 

```

---

### Post by vikram on 2008-01-10
typo on my part substitute /dev/sda1 for /dev/hdb1

sudo mount -t ntfs /dev/sda1 /media/hdb1
sudo /sbin/vol_id -u /dev/sda1

also did you try restarting in windows ?

---

### Post by spookyct on 2008-01-10
I have never had Windows installed on the drive...  it was always just a drive that had Media on it.

```
james@james-desktop:/media/hdb1$ sudo mount -t ntfs /dev/sda1 /media/hdb1
[sudo] password for james:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/hdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/hdb1 ntfs-3g defaults,force 0 0
james@james-desktop:/media/hdb1$ sudo /sbin/vol_id -u /dev/sda1
68D4807DD4804F6E
james@james-desktop:/media/hdb1$ 


```

---

### Post by Furat on 2008-01-10
Did you tried 
```
mount -t ntfs-3g /dev/sda1 /media/hdb1 -o force
```

---

### Post by spookyct on 2008-01-10
Sweet!  Got it back!  That was the next logical step...  i figured i'd wait for you though.

Thanks a lot!

---

