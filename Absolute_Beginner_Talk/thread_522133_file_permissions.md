---
title: "file permissions"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by B2thaB on 2007-08-10
Hello all,
I have a strange problem with file permissions. For Virtualbox I have to create a virtual hard disk, and I want to create it on my fat32 partition (/mnt/hda3). When I try to set it like this:

Type: Dynamically expanding image
Location: /mnt/hda3/virtual/winXP.vdi
Size: 2.00 GB (2147483648 Bytes)

I get this message:

Falied to create a hard disk image '/mnt/hda3/virtual/winXP.vdi' (VERR_ACCESS_DENIED).

Result Code:
0x80004005
Component:
VirtualDiskImage
Interface:
IVirtualDiskImage {a8265b5a-0d20-4a46-a02f-65693a4e8239}

So it seems that I don't have (write) access to that directory. But when I do a 'ls -l' I get this:
drwxrwxrwx 2 root root 32768 2007-08-10 11:03 virtual

So I think it should be possible to write to that dir.

After this I tried to change ownership of the dir from root to me, with the command: root@0[hda3]# chown bart /mnt/hda3/virtual
chown: changing ownership of `/mnt/hda3/virtual': Operation not permitted
???
Why can't I change permission when I am root?

Can somebody please point me in the right direction?
Thanks in advance.

---

### Post by shearn89 on 2007-08-10
try doing the first command, but put "sudo" in front of it. In ubuntu (and i think many other debian-based distros), we use "sudo" instead of logging in as the super user. Sudo stands for "super-user do". If the first command doesn't work still, try doing the second one ("chown bart ...."), but with sudo. Don't login as the admin.

---

### Post by B2thaB on 2007-08-10
@shearn89:
I'm sorry, I forgot to mention that I don't use Ubuntu, I use Mepis. Mepis is based on Ubuntu but does use the 'su' command and the root options.
I don't think this is a specific Mepis or Ubuntu problem, so thats why I posted it here.

---

### Post by schorsch on 2007-08-10
This seems to a problem regarding the mount options. Could you please send the output of the following commands:

```
mount
cat /etc/fstab
```

---

### Post by B2thaB on 2007-08-10
mount:
/dev/hda6 on / type ext3 (rw,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=100,mode=0622)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-desktop/volatile type tmpfs (rw)
/dev/hda3 on /mnt/hda3 type vfat (rw,nosuid,nodev,umask=000)
/dev/hda5 on /home type ext3 (rw,noatime)

bart@0[~]$ cat /etc/fstab
# Pluggable devices are handled by uDev, they are not in fstab
/dev/hda6 / ext3 defaults,noatime 1 1
/dev/hda7 swap swap sw,pri=1 0 0
/dev/hda3 /mnt/hda3 vfat auto,users,exec,rw,umask=000 0 0
none /proc proc defaults 0 0
none /proc/bus/usb usbfs devmode=0666 0 0
none /dev/pts devpts mode=0622 0 0
none /sys sysfs defaults 0 0
/dev/hda5 /home auto defaults,noatime 1 2
# Dynamic entries below
/dev/hda1 /mnt/hda1 vfat,ext3,ext2,reiserfs noauto,users,exec 0 0
/dev/hda2 /mnt/hda2 vfat,ext3,ext2,reiserfs noauto,users,exec 0 0
/dev/cdrom /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
/dev/hdb /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0


Mepis uses dynamic entries in fstab, but the drive I want to use (/mnt/hda3) is in the normal area of fstab. I edited fstab to mount /mnt/hda3 at startup, so maybe I did something wrong?

---

### Post by schorsch on 2007-08-10
Mounting the device with the following line in /etc/fstab should do the trick; for me it is working this way:

```
/dev/hda3 /mnt/hda3 vfat defaults,utf8,umask=022,gid=$GID,uid=$UID 0 1

```

with:

GID = your primary group-id
UID = your userid

You can get those values from the output of the "id" command. Finally do

```
umount /mnt/hda3
mount /mnt/hda3

```

and the problem should be fixed.

---

### Post by B2thaB on 2007-08-10
Thank you, that worked!

---

### Post by B2thaB on 2007-08-10
After a second look, that didn't work at all.
I could change ownership of the dir to bart, because I already owned it. 
Virtualbox still can't use the dir, and root stil can't change ownership of the dir.

The /mnt/hda3 is ok, I can use that disk for my purposes, but I really want Virtualbox to use the /mnt/hda3/virtual directory. But it is impossible to change ownership of the dir to vboxusers. The only way to change the ownership is via fstab and the whole /mnt/hda3 disk. 

Am I doing anything wrong here?

---

### Post by schorsch on 2007-08-10
Is vfat/fat32 able to store file/folder permissions? If I remember correctly only ntfs and the *nix filesystems are able to do so. In my environment there is no need to care about as I am the only user on this specific vfat-filesystem.
You should test, if you can change the entry in /etc/fstab so that the gid is that of the group vboxusers und also change the umask to "002" so that the group has write permissions. If all else fails you can even change the umask back to "000" but that would be a security issue.

---

### Post by bodhi.zazen on 2007-08-10
FAT and NTFS do not support Linux permissions/ownership.

They are set at the time of mount with 

uid=xxx
gid=yyy
umask=zzz

you can also have finer control with dmask and fmask

see man mount : [http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

---

### Post by schorsch on 2007-08-10
Ah, thanks for clearing this point, Bodhi!

---

### Post by B2thaB on 2007-08-11
Oh, so the problem is the fat32 disk.
I don't really care about security on that disk, becouse I use it as a music storage disk. 
I have already set the umask to 000, but virtualbox still can't create a virtual disk on /mnt/hda3/virtual. So maybe that is somekind of virtualbox problem/error.
If I edit fstab so that /mnt/hda3 belongs to me and the vboxusers group, I stil can't create a virtual disk on that mount. Even if I start the program as root I can't create a virtual disk.
Other programs can create files on /mnt/hda3, so I think it is some virtualbox problem.

And why can't my root account change the file permissions on that disk, is that becouse of the fat32 file system?

---

### Post by schorsch on 2007-08-11
Even root cannot change the permissions on fat32 filesystem; this will be handled by the mount options of the filesystem.

Are you trying to create a virtual disk with a fixed size or a dynamically expandable one? And which version of VirtualBox ae you using? I just tried to build a dynamically disk with VirtualBox 1.40 on my fat32 filesystem and it works. When building a disk with fixed size above 4 GB you get an error message that the file is to big. That seems to be a limitation of the filesystem itself. So even if you manage to create a virtual disk file on your fat32 partition you will probably run in this error with a dynamically growing disk when the disk file grows.

---

### Post by bodhi.zazen on 2007-08-11
> **B2thaB said:**
> And why can't my root account change the file permissions on that disk, is that becouse of the fat32 file system?

I do not know the answer to your virtual box problem.

In terms of ownership and permissions, however, the problem is FAT does not support linux ownership or permissions so you can not set them with chown or chmod.

HOWEVER you can set them at the time of mount via options (via either command line optionso ro options in /etc/fstab). See my previous posts or man mount.

---

### Post by B2thaB on 2007-08-11
Allright, so I have to set these options with fstab. 
I did change ownership of /mnt/hda3 to vboxusers, but that also didn't work. I used a dynamic virtual disk, and I use version 1.40. I really like that program, but now I have to use my /home folder for the virtual disk, and that is running out of space.

thanks for the info

---

### Post by schorsch on 2007-08-11
Sorry that I was not able to help you but I am simply not able to reproduce your problem .... it works like a charm with the mentioned entries in my fstab ....

---

