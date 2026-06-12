---
title: "Perrmission to Write to Fat32 partition"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-10-23
Here's my fstab:
/dev/hda7       /media/Leghorn  vfat    iocharset=utf8,umask=000  0    0
Don't know whether to change this,or do a chown thing. Please be explicit ! 
Thanks ! :)

---

### Post by aysiu on 2006-10-23
That looks fine to me.

Can you try these commands and see if you're still unable to write? ```
sudo umount /dev/hda7
sudo mkdir /media/Leghorn
sudo mount -a
``` If the second command tells you the directory already exists, that's fine--that's what we want to be sure of.

---

### Post by Drakkor on 2006-10-23
Ok,aysiu  all the commands worked,the second one as you said,already existed,
it seems funny to me,but yesterday it seems I could write to it fine, but now it says it's a read only disk !

---

### Post by aysiu on 2006-10-23
From that screenshot, everything looks good to me.

It's owned by root and is readable/writable by everyone.

---

### Post by Drakkor on 2006-10-23
Yeah,but unfortunately it's not,so after reading another thread that seemed to say that read/write fat32 is dicey, I'm just going to move the stuff out,and reformat it to ext3,lol :p

---

### Post by hyper_ch on 2006-10-23
r/w for fat32 should be fine... only ntfs is experimental as far as I know...

---

### Post by aysiu on 2006-10-23
Yes, read/write for FAT32 should be fine.

---

### Post by Drakkor on 2006-10-23
I read this: [http://www.ubuntuforums.org/showthread.php?t=163030&highlight=read+only+disk](http://www.ubuntuforums.org/showthread.php?t=163030&highlight=read+only+disk)

---

### Post by aysiu on 2006-10-23
> **Drakkor said:**
> I read this: [http://www.ubuntuforums.org/showthread.php?t=163030&highlight=read+only+disk](http://www.ubuntuforums.org/showthread.php?t=163030&highlight=read+only+disk)
I don't see what your point is.

---

### Post by Drakkor on 2006-10-23
I guess my point is that the original reason I had put in a fat32 partition,was to share it between Ubuntu/XP,and since in that thread other people also seem to be having problems with their fat32 partitions becoming read only,it seems to me,since I'm using less and less of windows,just to
go ahead and reformat it to ext3,so I can make use of it,it's 35GB which has
now become useless.

---

### Post by aysiu on 2006-10-23
If you want to format it as Ext3, go for it.

But that experience of it suddenly becoming read-only seems to be a freakish occurrence. It's not common.

---

### Post by noerej on 2006-10-25
Well, I had exactly the same problem. The reason you're getting these kernel panic messages is because there's something wrong with the filesystem. This can be corrected by using fsck.
First unmount the partition (or device in case of an external hdd/flash drive).
Then, run /sbin/fsck.vfat -a /dev/hda5. Of course you have to put your partition in place of hda5.
Worked for me, reading and writing happily to my external HDD!

---

### Post by mssever on 2006-10-25
If you type ```
mount
``` you'll see how your partition is actually being mounted. Note especially whether there's a ro or rw option. Explicitly setting rw in fstab might help. If it doesn't, you probably have a disk error.

---

### Post by Porta on 2006-10-25
I have the same trouble, can only read from a 40 Gb vfat partition.I have some important spreadsheets on there wich if i open them with openoffice come up 'read only'.
I cannot change ownership, permissions,in short:nothing.
The partition auto-mounts in /media and in fstab it has read/write permissions.
The only thing possible is to copy a file to /home, but don't try to save it to that partition, it's a big no,no
So what can i do? i am stuck with 40Gb of useless diskspace.

Greetings
Porta

---

### Post by mssever on 2006-10-25
First, cd to the partition directory and type ```
ls -l
```This will tell us what permissions are in effect. Since Windows filesystems don't support UNIX/Linux permissions, Ubuntu has to insert some. You can change the permissions by setting the umask in /etc/fstab. If you don't know how to do this, post the ls -l output and your fstab, and we'll help you. (The output of typing mount might also be helpful.)

---

### Post by Porta on 2006-10-25
Here is my output of 'ls -l':

drwxr-xr-x  5 root root   16384 2006-10-21 22:00 *******_backup
drwxr-xr-x  2 root root   16384 2006-05-12 07:12 access
-rwxr-xr-x  1 root root     268 2001-09-14 18:48 autoexec.bat
-rwxr-xr-x  1 root root  655276 2006-10-01 19:05 boc422.001
drwxr-xr-x  4 root root   16384 2006-10-21 22:14 ******_backup
drwxr-xr-x  2 root root   16384 2006-05-12 07:22 cfsnocd
-rwxr-xr-x  1 root root     159 2001-09-11 19:04 config.sys
drwxr-xr-x  2 root root   16384 2006-06-24 23:22 excel
drwxr-xr-x  4 root root   16384 2006-10-01 19:44 Exefiles
drwxr-xr-x  2 root root   16384 2006-05-12 07:22 Gibson
drwxr-xr-x  3 root root   16384 2006-06-06 10:55 home
drwxr-xr-x  3 root root   16384 2006-05-12 07:11 K9Backup
drwxr-xr-x  2 root root   16384 2006-06-25 14:40 openoffice
drwxr-xr-x  3 root root   16384 2006-05-12 07:12 Profilescomp2
drwxr-xr-x  3 root root   16384 2006-05-12 07:13 ProfilesSU
drwxr-xr-x  3 root root   16384 2006-05-12 07:19 ProfilesTB
drwxr-xr-x  3 root root   16384 2006-05-24 17:23 ProxoBackup
drwxr-xr-x  2 root root   16384 1999-02-04 13:28 recycled
drwxr-xr-x  4 root root   16384 2006-05-12 07:24 RegCleaner
drwxr-xr-x  2 root root   16384 2006-05-12 07:13 Sleutelssoftware
drwxr-xr-x  2 root root   16384 2003-08-29 19:49 System Volume Information
drwxr-xr-x  3 root root   16384 2006-05-12 07:18 visio
-rwxr-xr-x  1 root root   16384 2005-02-04 00:31 vsnap.idx
-rwxr-xr-x  1 root root  867640 2006-10-11 10:35 WindowsXP-KB922819-x86-NLD.exe
-rwxr-xr-x  1 root root  731448 2006-10-11 10:35 WindowsXP-KB923414-x86-NLD.exe
-rwxr-xr-x  1 root root 1115448 2006-10-11 10:35 WindowsXP-KB924191-x86-NLD.exe
-rwxr-xr-x  1 root root 1683256 2006-10-11 10:35 WindowsXP-KB924496-x86-NLD.exe
drwxr-xr-x 11 root root   16384 2006-05-12 07:17 word
drwxr-xr-x  2 root root   16384 2006-06-26 14:10 XPupdate
drwxr-xr-x  3 root root   16384 2006-05-12 07:16 Zippie

And this is fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda5       /media/win      vfat     auto,rw,user       0       0

Greetings
Porta

---

### Post by Porta on 2006-10-25
And here is the output of 'mount':

****@****-desktop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/hda5 on /media/win type vfat (rw,noexec,nosuid,nodev)

That was  a lot of copy/paste action. :D 

Greetz
Porta

---

### Post by hk_2999 on 2006-10-25
*[COLOR="Red"]*reedited for clarity*[/COLOR]*

This happened to me before. I've got a 30GB FAT32 disk handy to store all my files and share them with WinXP. Anyway, I upgraded to edgy beta so that solved my problem.

The problem is caused because something probably messed with your bootup settings, an installer, a livecd or just a quick mistake probably.

The easiest, most efficient though no-brainer solution would be:

*Step 1:* Tell fstab not to let root mount the partition automatically, and allow users to remount it at boot
```
/dev/hda7 /media/Leghorn vfat user,noauto,rw 0 0
```

i dont see the point of umask and iocharset, since in my experience those things are set up automatically, but i can be wrong, so maybe you should put them back there.

*Step 2:* Click your way to System->Preferences->Sessions->Startup Programs->Add and type ```
mount /media/Leghorn
```, Close and restart, test, i'm sure it'll work fine now.

---

### Post by bodhi.zazen on 2006-10-25
> **Porta said:**
> Greetz
Porta

Try this fstab entry:```
/dev/hda5 /media/win vfat auto,rw,user,gid=100,umask=000 0 0
```

---

### Post by mssever on 2006-10-25
> **Porta said:**
> Here is my output of 'ls -l':

drwxr-xr-x  5 root root   16384 2006-10-21 22:00 *******_backup
drwxr-xr-x  2 root root   16384 2006-05-12 07:12 access
-rwxr-xr-x  1 root root     268 2001-09-14 18:48 autoexec.bat
-rwxr-xr-x  1 root root  655276 2006-10-01 19:05 boc422.001
drwxr-xr-x  4 root root   16384 2006-10-21 22:14 ******_backup
drwxr-xr-x  2 root root   16384 2006-05-12 07:22 cfsnocd
-rwxr-xr-x  1 root root     159 2001-09-11 19:04 config.sys
drwxr-xr-x  2 root root   16384 2006-06-24 23:22 excel
drwxr-xr-x  4 root root   16384 2006-10-01 19:44 Exefiles
drwxr-xr-x  2 root root   16384 2006-05-12 07:22 Gibson
drwxr-xr-x  3 root root   16384 2006-06-06 10:55 home
drwxr-xr-x  3 root root   16384 2006-05-12 07:11 K9Backup
drwxr-xr-x  2 root root   16384 2006-06-25 14:40 openoffice
drwxr-xr-x  3 root root   16384 2006-05-12 07:12 Profilescomp2
drwxr-xr-x  3 root root   16384 2006-05-12 07:13 ProfilesSU
drwxr-xr-x  3 root root   16384 2006-05-12 07:19 ProfilesTB
drwxr-xr-x  3 root root   16384 2006-05-24 17:23 ProxoBackup
drwxr-xr-x  2 root root   16384 1999-02-04 13:28 recycled
drwxr-xr-x  4 root root   16384 2006-05-12 07:24 RegCleaner
drwxr-xr-x  2 root root   16384 2006-05-12 07:13 Sleutelssoftware
drwxr-xr-x  2 root root   16384 2003-08-29 19:49 System Volume Information
drwxr-xr-x  3 root root   16384 2006-05-12 07:18 visio
-rwxr-xr-x  1 root root   16384 2005-02-04 00:31 vsnap.idx
-rwxr-xr-x  1 root root  867640 2006-10-11 10:35 WindowsXP-KB922819-x86-NLD.exe
-rwxr-xr-x  1 root root  731448 2006-10-11 10:35 WindowsXP-KB923414-x86-NLD.exe
-rwxr-xr-x  1 root root 1115448 2006-10-11 10:35 WindowsXP-KB924191-x86-NLD.exe
-rwxr-xr-x  1 root root 1683256 2006-10-11 10:35 WindowsXP-KB924496-x86-NLD.exe
drwxr-xr-x 11 root root   16384 2006-05-12 07:17 word
drwxr-xr-x  2 root root   16384 2006-06-26 14:10 XPupdate
drwxr-xr-x  3 root root   16384 2006-05-12 07:16 Zippie

And this is fstab:


OK. Change your fstab to this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda5       /media/win      vfat     auto,rw,user**[COLOR=Red],uid=1000,gid=1000,fmask=111,dmask=000,shortname=mixed[/COLOR]**       0       0
``` Then, type ```
sudo umount /media/win; sudo mount /media/win
```

---

### Post by Porta on 2006-10-25
Oke, i will try this out and report back, thanks for now. :p 

regards
Porta

---

### Post by Porta on 2006-10-25
mssever, your advice did the trick, great stuff!! ,i can use my spreadsheets again.
Thanks for the help in this.
Now i have to read up on this provided information :D

Regards
Porta

---

