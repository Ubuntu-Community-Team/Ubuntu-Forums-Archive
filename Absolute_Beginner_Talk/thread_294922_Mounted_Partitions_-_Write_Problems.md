---
title: "Mounted Partitions - Write Problems"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by indytim on 2006-11-07
It's been quite awhile since I had to do the basics, so please bear with me.

The problem is that I am not able to write to ext3 partitons via Nautilus.  I had to do a fresh install of Dapper Gnome and need to write to these partitions.  They are mounting ok, just can't write to them.  The one causing problems right now is sda12 but the same problem exists across all of the ext3 partitons (except the root),

Attaching my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda10      /media/sda10    ext3    defaults        0       2
/dev/sda11      /media/sda11    vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda12      /media/sda12    ext3    defaults        0       2
/dev/sda8       /media/sda8     ext3    defaults        0       2
/dev/sda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Thanks,

IndyTim

---

### Post by taurus on 2006-11-07
Try using the sudo command from a terminal or 

```
gksudo nautilus
```

---

### Post by indytim on 2006-11-07
Thanks Taurus.

I want to have write access via Nautilus by default rather than do the terminal thing everytime I write a file/folder to one of these partitions.

Tx,

IndyTim

---

### Post by taurus on 2006-11-07
For ext3 partition(s), you can change permission with chmod...

```
sudo chmod -R 777 directory
```

---

### Post by bodhi.zazen on 2006-11-07
Edit fstab.```
gksudo gedit /etc/fstab
```

Add options to include auto,users,gid=100,umask=000

ie```
/dev/sda8  /media/sda8  ext3  auto,users,gid=100,umask=000  0  2
```

Unmount the partitions, and re-mount them (as a user, not with sudo)

```
sudo umount /media/sda8
mount /media/sda8
```

[See also how to fstab](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by indytim on 2006-11-07
After creating the folders in the partition via gksudo nautilus, I was able to change the group and individual owership via the properties.

As I said, it's been a while...

Thanks Again,

IndyTim

---

### Post by bodhi.zazen on 2006-11-07
If you do not edit fstab your permissions will likely change again on re-boot or re-mount.

---

### Post by Fabiano Shark on 2006-11-07
I'm dealing with exactly the same problem since three days ago... after much [SFTW]("http://www.google.com.br/search?hs=CGV&hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&q=define%3ASTFW&btnG=Pesquisar&meta=")ed for these days, I decided to ask for help here... :oops: 

> 
fshark@fshark:~$ sudo fdisk -l

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          61      489951   82  Linux swap / Solaris
/dev/sda2              62        4863    38572065   83  Linux
/dev/sda3            4864        9729    39086145   83  Linux
/dev/hdd1               1          73      586341   82  Linux swap / Solaris
/dev/hdd2              74        1897    14651280   83  Linux
**/dev/hdd3            1898        9733    62942670   83  Linux**


I'm trying to mount hdd3 with read and write permissions for users as default. Like this, only root can write on it:

> 
fshark@fshark:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=05c1221f-21ca-4ba8-844a-12f640f4172a / ext3 defaults,errors=remount-ro 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=3a85f206-3be1-4d43-b0be-7e474d6669d4 /home ext3 defaults 0 2
# /dev/sda1 -- converted during upgrade to edgy
UUID=8ae8b146-0ddd-402a-a3fe-77f50581cada none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/hdd2 -- converted during upgrade to edgy
UUID=e4adb4a2-5eb5-444d-a974-1a7140bf9a46 /mnt/hdda ext3 defaults 0 0
# /dev/hdd3 -- converted during upgrade to edgy
**UUID=4ecb3ffd-0861-426b-88a1-ddad66a3850d /mnt/hddb ext3 defaults 0 0**


**I tried almost all (logical) combinations existent for *options* of *fstab*, and as I said, no one worked, but so, this is the last one:**

> 
fshark@fshark:~$ sudo mkdir /mnt/hddb
fshark@fshark:~$ ls -l /mnt | grep hddb
drwxr-xr-x  2 root   root   4096 2006-11-01 16:39 hddb
fshark@fshark:~$ sudo umount /dev/hdd3
fshark@fshark:~$ id
uid=1000(fshark) gid=1000(fshark) 
fshark@fshark:~$ gksudo gedit /etc/fstab


> 
fshark@fshark:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=05c1221f-21ca-4ba8-844a-12f640f4172a / ext3 defaults,errors=remount-ro 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=3a85f206-3be1-4d43-b0be-7e474d6669d4 /home ext3 defaults 0 2
# /dev/sda1 -- converted during upgrade to edgy
UUID=8ae8b146-0ddd-402a-a3fe-77f50581cada none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/hdd2 -- converted during upgrade to edgy
UUID=e4adb4a2-5eb5-444d-a974-1a7140bf9a46 /mnt/hdda ext3 defaults 0 0
# /dev/hdd3 -- converted during upgrade to edgy
**UUID=4ecb3ffd-0861-426b-88a1-ddad66a3850d /mnt/hddb ext3 auto,users,gid=1000,umask=000  0  2**


> 
fshark@fshark:~$ mount /mnt/hddb/
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/4ecb3ffd-0861-426b-88a1-ddad66a3850d,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


*I did this following the steps of bodhi.zazen posted here.




But I also tried this:

**UUID=4ecb3ffd-0861-426b-88a1-ddad66a3850d /mnt/hddb ext3 auto,users,rw  0  2**

> 
fshark@fshark:~$ mount /mnt/hddb
fshark@fshark:~$ ls -l /mnt | grep hddb
drwxrwxr-x  5 fshark fshark 4096 2006-05-27 19:17 hddb
fshark@fshark:~$ mkdir /mnt/hddb/fshark/TEST
mkdir: cannot create directory `/mnt/hddb/fshark/TEST': Read-only file system


This is the message I've been reading for all these three days... ](*,)

---

### Post by bodhi.zazen on 2006-11-07
[list=number][*]What is the output of **dmesg | tail or so**.
[*]What happens if you do it one step at a time, **mdkir /mnt/hddb/fshark/** then **/mnt/hddb/fshark/TEST**.
[*] Change your gid to 100 (I am not sure if 1000 is you GID or UID) **UUID=4ecb3ffd-0861-426b-88a1-ddad66a3850d /mnt/hddb ext3 auto,users,[color=red]gid=100[/color],umask=000 0 2**[/list]

After editing fstab, umount and re-mount the partition.

---

### Post by dannyboy79 on 2006-11-07
if these are removable devices, which most of the time anything under media is, then you need to completely remove the fstab entry because pmount is a wrapper for mount which automagically mounts these with write permission for users. read man pmount. also check out this thread, also a tip, use the search feature before posting a thread this way there isn't the same question over and over, just a thought.

[http://www.ubuntuforums.org/showthread.php?t=291849&highlight=usb](http://www.ubuntuforums.org/showthread.php?t=291849&highlight=usb)

---

### Post by dannyboy79 on 2006-11-07
> **bodhi.zazen said:**
> [list=number][*]What is the output of **dmesg | tail or so**.
[*]What happens if you do it one step at a time, **mdkir /mnt/hddb/fshark/** then **/mnt/hddb/fshark/TEST**.
[*] Change your gid to 100 (I am not sure if 1000 is you GID or UID) **UUID=4ecb3ffd-0861-426b-88a1-ddad66a3850d /mnt/hddb ext3 auto,users,[color=red]gid=100[/color],umask=000 0 2**[/list]

After editing fstab, umount and re-mount the partition.

FYI, the 1st user in ubuntu after root is always 1000 as well as the group id is 1000.

---

### Post by Fabiano Shark on 2006-11-07
1. The output is:
> 
[17187297.772000] EXT3-fs: Unrecognized mount option "gid=1000" or missing value
[17187312.628000] EXT3-fs: Unrecognized mount option "gid=1000" or missing value
[17187316.892000] EXT3-fs: Unrecognized mount option "gid=1000" or missing value
[17187328.280000] EXT3-fs: Unrecognized mount option "gid=1000" or missing value


2. I can't create /mnt/hddb/fshark cause this folder already exist in hddb.

3. The dmesg for [COLOR="Red"]gid=100[/COLOR] is:
> 
[17190016.696000] EXT3-fs: Unrecognized mount option "gid=100" or missing value

> 
fshark@fshark:~$ id
uid=1000(fshark) gid=1000(fshark)


Any idea?

---

### Post by Fabiano Shark on 2006-11-07
> Originally Posted by **dannyboy79**:

if these are removable devices, which most of the time anything under media is, then you need to completely remove the fstab entry because pmount is a wrapper for mount which automagically mounts these with write permission for users. read man pmount. also check out this thread, also a tip, use the search feature before posting a thread this way there isn't the same question over and over, just a thought.

[http://www.ubuntuforums.org/showthre...&highlight=usb](http://www.ubuntuforums.org/showthre...&highlight=usb)

No it isn't. It is a hard disk. :-?

---

### Post by bodhi.zazen on 2006-11-07
> **dannyboy79 said:**
> FYI, the 1st user in ubuntu after root is always 1000 as well as the group id is 1000.

Thanks. I was trying to mount with group = users.

---

### Post by bodhi.zazen on 2006-11-07
> **Fabiano Shark said:**
> 1. The output is:


2. I can't create /mnt/hddb/fshark cause this folder already exist in hddb.

3. The dmesg for [COLOR="Red"]gid=100[/COLOR] is:



Any idea?


I assumed you tried without gid=1000?

**auto,users,umask=000**

OR

**auto,users,uid=1000,gid=100,umask=000**

---

### Post by Fabiano Shark on 2006-11-07
> **bodhi.zazen said:**
> I assumed you tried without gid=1000?

**auto,users,umask=000**


[17192100.792000] EXT3-fs: Unrecognized mount option "umask=000" or missing value


> 
OR

**auto,users,uid=1000,gid=100,umask=000**

fshark@fshark:~$ sudo dmesg -c "mount /mnt/hddb"
[17192311.956000] EXT3-fs: Unrecognized mount option "uid=1000" or missing value

:-?

---

### Post by bodhi.zazen on 2006-11-07
OK, let's try something else then.

fstab otpions: **auto,users**

```
sudo umount /mnt/hddb
sudo mount /mnt/hddb/
sudo chmod 777 /mnt/hddb
sudo chown fshark:fshark
```

Now what is the outome?

Can you unomunt and remount as a user?

---

### Post by dannyboy79 on 2006-11-07
guys, using the gid, uid, umask, fmask, etc etc are only applicable fstab options for vfat, not EXT3. do a man fstab which will tell you to do man mount for filesytem mount options and you'll find out what options you can use.

my fstab entry for a ext3 drive that I use for storage is as follows:
/dev/hdd1       /home/daniel/300gb-ext3 ext3    defaults        0       2

and then of course u need to make sure you chown, chgrp, and chmod the mount points for correct permission and write accesss.

---

### Post by Fabiano Shark on 2006-11-07
> **bodhi.zazen said:**
> OK, let's try something else then.

fstab otpions: **auto,users**

```
sudo umount /mnt/hddb
sudo mount /mnt/hddb/
sudo chmod 777 /mnt/hddb
sudo chown fshark:fshark
```

Now what is the outome?

Can you unomunt and remount as a user?

Well, it works fine while I'm was logged in the system, when I reeboted it, in the middle of Ubuntu's loading, this error appears:

```

/home: clean, 2049/48892448 files, ... blocks.
/home contains a file with errors, check forced.
/home: 
Inode 950305 has illegal blocks.

```

So I enter the root password and change fstab otpions from **auto,users** to **noauto,users** for Ubuntu starts.

And yes, I can mount as a user.

:-?

---

### Post by bodhi.zazen on 2006-11-07
> **Fabiano Shark said:**
> Well, it works fine while I'm was logged in the system, when I reeboted it, in the middle of Ubuntu's loading, this error appears:

```

/home: clean, 2049/48892448 files, ... blocks.
/home contains a file with errors, check forced.
/home: 
Inode 950305 has illegal blocks.

```

So I enter the root password and change fstab otpions from **auto,users** to **noauto,users** for Ubuntu starts.

And yes, I can mount as a user.

:-?

I do not think that error message has anything to do with your fstab options.

I would advise you run fsck:

```
sudo e2fsck -y /dev/hdd3
```

---

### Post by Fabiano Shark on 2006-11-07
> **dannyboy79 said:**
> guys, using the gid, uid, umask, fmask, etc etc are only applicable fstab options for vfat, not EXT3. do a man fstab which will tell you to do man mount for filesytem mount options and you'll find out what options you can use.

my fstab entry for a ext3 drive that I use for storage is as follows:
/dev/hdd1       /home/daniel/300gb-ext3 ext3    defaults        0       2

and then of course u need to make sure you chown, chgrp, and chmod the mount points for correct permission and write accesss.

Yeah, maybe you're right that in man's pages have my solutinons, but I didn't found it... :-| 

As I said, my line was like this, but the folders permissions were:

```
fshark@fshark:~$ ls -l /mnt | grep hddb
drwxr-xr-x 2 root root 4096 2006-11-01 16:39 hddb

```

And now, (before mounting, of course) is like this:
```

fshark@fshark:~$ ls -l /mnt | grep hddb
drwxrwxrwx 2 root root 4096 2006-11-01 16:39 hddb

```

It only works while I was logged in the system, on the boot-up it crashed again, and showed the same error again, so I *commented* the line and *halted* the system to make it starts.

Question: This **/dev/hdd3** is the */home* of the **/dev/hdd**, does it have any problem? :confused:

---

### Post by Fabiano Shark on 2006-11-07
> **bodhi.zazen said:**
> I do not think that error message has anything to do with your fstab options.

I would advise you run fsck:

```
sudo e2fsck -y /dev/hdd3
```

I did what you advised trusting on your beans...

```
/home: ***** FILE SYSTEM WAS MODIFIED *****
/home: 179366/7880704 files (3.8% non-contiguous), 14142911/15735667 blocks

```

---

### Post by bodhi.zazen on 2006-11-07
And did that fix your error message at boot? (you should be able to go back to **auto,users**).

Thank you for your trust !

---

### Post by Fabiano Shark on 2006-11-07
> **bodhi.zazen said:**
> And did that fix your error message at boot? (you should be able to go back to **auto,users**).

Thank you for your trust !

Now, after yours advise to run fsck and with dannyboy79's tip, my hddb is mounted at the boot-up and no errors at all. I restarted the system twice. :) 

But... every time after enters the login and password at GDM, an alert message shows-up:

```

Users's %HOME/.dmrc file being ignored, this prevents the default session and langage from being saved.
File should be owned by user and have 644 permissions.
``` 

```
fshark@fshark:~$ ls -al | grep .dmrc
-rw-r--r--  1 fshark fshark      26 2006-10-31 17:43 .dmrc

fshark@fshark:~$ ls /mnt/hddb/fshark/ -al | grep .dmrc
-rw-------  1 fshark fshark      26 2006-05-27 18:01 .dmrc


```

Should I remove this second one? :-k

---

### Post by bodhi.zazen on 2006-11-07
> **Fabiano Shark said:**
> Now, after yours advise to run fsck and with dannyboy79's tip, my hddb is mounted at the boot-up and no errors at all. I restarted the system twice. :) 

But... every time after enters the login and password at GDM, an alert message shows-up:

```

Users's %HOME/.dmrc file being ignored, this prevents the default session and langage from being saved.
File should be owned by user and have 644 permissions.
``` 

```
fshark@fshark:~$ ls -al | grep .dmrc
-rw-r--r--  1 fshark fshark      26 2006-10-31 17:43 .dmrc

fshark@fshark:~$ ls /mnt/hddb/fshark/ -al | grep .dmrc
-rw-------  1 fshark fshark      26 2006-05-27 18:01 .dmrc


```

:-k

LOL :lol:

Try this fix:```
sudo chmod 644 .dmrc
sudo chmod 755 /home/user_name
```
And make sure you are the owner of /home/fshark (? /mnt/hddb/fshark).

---

### Post by Fabiano Shark on 2006-11-07
> **bodhi.zazen said:**
> LOL :lol:

Try this fix:```
sudo chmod 644 .dmrc
sudo chmod 755 /home/user_name
```
And make sure you are the owner of /home/fshark (? /mnt/hddb/fshark).

**BEFORE:**
```
fshark@fshark:~$ ls -al | grep .dmrc
-rw-r--r--  1 fshark fshark      26 2006-10-31 17:43 .dmrc

fshark@fshark:~$ ls -al /mnt/hddb/fshark | grep .dmrc
-rw-------  1 fshark fshark      26 2006-05-27 18:01 .dmrc

```

**NOW:**
```
fshark@fshark:~$ ls -al | grep .dmrc
-rwxr-xr-x  1 fshark fshark      26 2006-10-31 17:43 .dmrc

fshark@fshark:~$ ls -al /mnt/hddb/fshark | grep .dmrc
-rw-r--r--  1 fshark fshark      26 2006-05-27 18:01 .dmrc

```

Same message :-k

---

