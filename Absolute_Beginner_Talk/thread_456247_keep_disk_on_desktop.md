---
title: "keep disk on desktop?"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by thelegionnaire on 2007-05-27
so how do i keep my windows partition permanently on my desktop, and with write-access?

---

### Post by taurus on 2007-05-27
What filesystem is that Windows partition and have you mounted it and to where (mount point)?

---

### Post by thelegionnaire on 2007-05-27
im pretty new at this and dont have an answer to either question, if i could get a bit more help?...

---

### Post by taurus on 2007-05-27
Open a terminal, Applications -> Accessories -> Terminal, and post the output of these commands.

```
sudo fdisk -l <-- That is a lower case letter l as in larry, not number 1.
cat /etc/fstab
```

---

### Post by thelegionnaire on 2007-05-27
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8954    71922973+   7  HPFS/NTFS
/dev/hda2            8955       10393    11558767+  83  Linux
/dev/hda3           10464       11874    11333857+   7  HPFS/NTFS
/dev/hda4           10394       10463      562275    5  Extended
/dev/hda5           10394       10463      562243+  82  Linux swap / Solaris

Partition table entries are not in disk order
m@m-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=8205b9e1-8b2d-4879-8759-dbc6dcb2aa97 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=a1871188-7e70-4720-9f1b-75859bc21a66 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2007-05-27
I guess you want to mount /dev/hda1 and /dev/hda3.  Which release are you running right now (Dapper, Edgy, or Feisty) because you first need to install ntfs-3g and ntfs-config before you can mount them with read/write permissions.

---

### Post by thelegionnaire on 2007-05-27
i am using feisty, but i installed both of those just now using synaptic, i figure thats what you were gonna tell me to do, now what?

---

### Post by taurus on 2007-05-27
Yip.  After you have installed those two packages, open a terminal and run the ntfs-config to configure those two ntfs partitions.

```
gksudo ntfs-config
```

---

### Post by thelegionnaire on 2007-05-27
** (ntfs-config:7013): WARNING **: Mounting /media/HDA1 failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hda1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

so i got this for both of them, i've been having alot of trouble with windows lately, and cannot do a clean shutdown, and when i boot into windows it wants to scandisk, but wont work if i let it, should i try this:ntfsfix? as i do not have vista

---

### Post by taurus on 2007-05-27
Let's see if you can mount it from a command first before you run ntfsfix.

```
sudo mkdir /media/hda1
sudo mount -t ntfs /dev/hda1 /media/hda1
df -h
```

---

### Post by thelegionnaire on 2007-05-27
m@m-laptop:~$ sudo mkdir /media/hda1
mkdir: cannot create directory `/media/hda1': File exists
m@m-laptop:~$ sudo mount -t ntfs /dev/hda1 /media/hda1
m@m-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              11G  3.3G  7.1G  32% /
varrun                502M  108K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M  100K  502M   1% /proc/bus/usb
udev                  502M  100K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   39M  464M   8% /lib/modules/2.6.20-15-generic/volatile
/dev/hda1              69G   56G   13G  82% /media/hda1


not really sure what this means

---

### Post by taurus on 2007-05-27
> **thelegionnaire said:**
> m@m-laptop:~$ sudo mkdir /media/hda1
mkdir: cannot create directory `/media/hda1': File exists
m@m-laptop:~$ sudo mount -t ntfs /dev/hda1 /media/hda1
m@m-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              11G  3.3G  7.1G  32% /
varrun                502M  108K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M  100K  502M   1% /proc/bus/usb
udev                  502M  100K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   39M  464M   8% /lib/modules/2.6.20-15-generic/volatile
[COLOR="Blue"]/dev/hda1              69G   56G   13G  82% /media/hda1[/COLOR]

not really sure what this means

It means that you have successfully mounted /dev/hda1 to /media/hda1.  Do you need to recover data from it since you can't boot into XP anymore?

---

### Post by thelegionnaire on 2007-05-27
wow, cool. so i do the same for hda3?

and i can boot into xp as long as i dont do a scandisk

---

### Post by taurus on 2007-05-27
```
sudo mkdir /media/hda3
sudo umount /dev/hda1
sudo mount -t ntfs /dev/hda1 /media/hda1 -o nls=utf8,umask=0222
sudo mount -t ntfs /dev/hda3 /media/hda3 -o nls=utf8,umask=0222
df -h
```
Now, you can read both /media/hda1 and /media/hda3 but you cannot write to them.

---

### Post by thelegionnaire on 2007-05-27
so how do i write to them?

---

### Post by taurus on 2007-05-27
If you want to write to them, ntfs, you need to use ntfs-3g driver since ntfs is only for read-only.  See if this works.

```
sudo umount /dev/hda1
sudo mount -t ntfs-3g /dev/hda1 /media/hda1
ls -la /media
```

---

### Post by thelegionnaire on 2007-05-27
also this is what i got:
m@m-laptop:~$ sudo mkdir /media/hda3
mkdir: cannot create directory `/media/hda3': File exists
m@m-laptop:~$ sudo umount /dev/hda1
umount: /dev/hda1: not mounted
m@m-laptop:~$ sudo mount -t ntfs /dev/hda1 /media/hda1 -o nls=utf8,umask=0222
m@m-laptop:~$ sudo mount -t ntfs /dev/hda3 /media/hda3 -o nls=utf8,umask=0222
m@m-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              11G  3.3G  7.1G  32% /
varrun                502M  108K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M  100K  502M   1% /proc/bus/usb
udev                  502M  100K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   39M  464M   8% /lib/modules/2.6.20-15-generic/volatile
/dev/hda1              69G   56G   13G  82% /media/hda1
/dev/hda3              11G   65M   11G   1% /media/hda3


and i cannot see either drive now, whereas before i could but had to put a password eachtime to get readonly access

---

### Post by thelegionnaire on 2007-05-27
and the ntfs-3g didnt work, it said the drive was shut down improperly

---

### Post by taurus on 2007-05-27
> **thelegionnaire said:**
> and the ntfs-3g didnt work, it said the drive was shut down improperly

That's what I figure.  So, you need to either boot into XP and shut it down properly if you want to write to it from Ubuntu or just use ntfs to read from it.  Or, you can run ntfsfix if you want but if you damage your XP from running that command in Ubuntu and can't even boot XP, I have nothing to do with it.

---

### Post by thelegionnaire on 2007-05-27
but you see, i cant even access those drives anymore, wheras before i could, but read only, so no i'm worse off than i started

---

### Post by taurus on 2007-05-27
What do you mean you can't access them anymore?  What's the output of this command then?

```
ls -la /media/hda1
```

---

