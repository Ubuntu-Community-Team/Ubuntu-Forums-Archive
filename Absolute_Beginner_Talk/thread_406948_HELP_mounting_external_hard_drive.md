---
title: "HELP mounting external hard drive"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by nynoah on 2007-04-11
I just bought a seagate external hard drive.  I can see it on my computer but I can not write to it.   I am also under the KDE interface right now.  Help what do i have to do to get this to work?

---

### Post by LaurelLynn on 2007-04-11
Dear nynoah,

It may have come preformatted with NTFS.  If so you can either use gparted to repartition it, or download the ntfs-3g drivers.  Instructions can be found at the project website:

[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

### Post by nynoah on 2007-04-11
Ok I reformated it to FAT32.................But I still can not write to the drive.  Any sugestions.  I already enabled it in the systems settings area and that has not helped.

---

### Post by LaurelLynn on 2007-04-11
Dear nynoah,

Please use Copy and Paste to post the results of the following commands:

cat /etc/fstab

df -lh

It will give me a better  idea what might be going on.

---

### Post by nynoah on 2007-04-11
noah@noah-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=c7c6d983-d5ce-43ba-bca3-acf1bcc64535 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
UUID=24683A6B683A3C3C /media/sda1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda5
UUID=6023622b-ebac-4d3d-9bc3-57e4e8684bd5 none swap sw 0 0
/dev/hdb /media/cdrom0 auto user,atime,auto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdc1 /media/FreeAgent\040Drive/System\040Volume\040Information auto users,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/sdb1 /media/exthd auto users,atime,auto,rw,dev,noexec,suid 0 0
noah@noah-desktop:~$ df -lh
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             164G   68G   88G  44% /
varrun                506M  160K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  100K   10M   1% /proc/bus/usb
udev                   10M  100K   10M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-11-generic/volatile
/dev/sda1              65G  5.9G   60G   9% /media/sda1
/dev/sdb1             298G   16K  298G   1% /media/exthd
noah@noah-desktop:~$

---

### Post by nynoah on 2007-04-11
Thanks for helping me out too :)

---

### Post by nynoah on 2007-04-11
I m not sure if I have extra ghost drives mounted becuase I was trying to fix this.   What my system has is one SATA hard drive, one 3.5 floppy, and ond DVD writier drive.  With my external  USB Seagate HD that is 300 Gig.

---

### Post by LaurelLynn on 2007-04-11
Ok,

I actually see three serial drives.  /dev/sda seems to be the internal drive with the operating system.

Also /dev/sdb:

/dev/sdb1 /media/exthd auto users,atime,auto,rw,dev,noexec,suid 0 0

Looks like an external hard drive.  Settings look ok. And matches with:

/dev/sdb1 298G 16K 298G 1% /media/exthd

So that drive is mounted. You should be able to ¨ls /media/exthd¨ to list it´s root folder.  The only thing I see that might cause a problem is the use of ¨auto¨ for a format.  Since you said you formatted  Fat32, if that is the right external drive ( and it is the size you discribed. ),  I would try replacing  ¨auto¨ with ¨vfat¨.

$ sudo umount  /media/exthd

Edit fstab (make a copy of it first, just in case):

$ sudo mount  /media/exthd

The other entry  /dev/sdc:

/dev/sdc1 /media/FreeAgent\040Drive/System\040Volume\040Information auto users,atime,noauto,rw,nodev,noexec,nosuid 0 0

This one worries me a bit.  Mostly because it looks like an attempt to use a Windows filename on a Linux system.  Each handles slashs and some other characters differently.

 Also I don´t see any mention of it in the ¨df¨ listing.  Implying that it is not mounted.

I suspect it is a recovery partition SO LEAVE IT ALONE if you don´t know what it is.

If this is a drive you recognize, it could be from Ghost,  and you want to access it, I would comment it out with a ¨#¨ in front:

# /dev/sdc1 /media/FreeAgent\040Drive/System\040Volume\040Information auto users,atime,noauto,rw,nodev,noexec,nosuid 0 0

And try something like this instead:

 /dev/sdc1 /media/extharddrive  auto users,atime,noauto,rw,nodev,noexec,nosuid 0 0

The same thing I said about ¨auto¨ above would also apply. After editting try:

$ mkdir /media/extharddrive
$ sudo mount  /media/extharddrive

They should then show up in the ¨df¨ listing.

---

### Post by nynoah on 2007-04-11
Ok I deleted the one you were talking about and changed the other to VFAT  and ran the comands you gave me before.......HEre is what I have now

noah@noah-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=c7c6d983-d5ce-43ba-bca3-acf1bcc64535 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
UUID=24683A6B683A3C3C /media/sda1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda5
UUID=6023622b-ebac-4d3d-9bc3-57e4e8684bd5 none swap sw 0 0
/dev/hdb /media/cdrom0 auto user,atime,auto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdb1 /media/exthd vfat uid=0,gid=0,noauto,ro,nouser 0 0
noah@noah-desktop:~$ df -lh
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             164G   69G   87G  45% /
varrun                506M  160K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  100K   10M   1% /proc/bus/usb
udev                   10M  100K   10M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-11-generic/volatile
/dev/sda1              65G  5.9G   60G   9% /media/sda1
/dev/sdb1             298G   16K  298G   1% /media/exthd
noah@noah-desktop:~$

---

### Post by nynoah on 2007-04-11
And i still can not write to the hard drive.  I swear I love Ubuntu and hate it all at the same time.  This should be easier than it is.

:(

---

### Post by LaurelLynn on 2007-04-11
Hmmm,

/media/exthd  looks like it is there.  If you still can´t write it might be a permission problem. Pick some file on your Desktop, or copy something there.  Then try:

$ sudo cp ~/Desktop/the-filename   /media/exthd
$  ls /media/exthd

If it appears there then the permissions are the problem. Then try:

$ sudo chmod ugo=rwx   /media/exthd

That should give everyone total access to the drive.  Try the two  commands above again on a different file, only this time without the sudo. If it copies all should be well.

Let me know if there are any error messages.  I have to leave for 4-6 hours, but I will check back latter to see how you are doing.

---

### Post by nynoah on 2007-04-11
Ok I can do it on a comand line to drop a file in, but I still can not get it to be able to cut and past anything into it.  It is still saying that I do not have permission.

Noah

---

### Post by nynoah on 2007-04-11
It also denies me from doing the comand line if I do not use Sudo.

---

### Post by nynoah on 2007-04-11
also the code you gave me

sudo chmod ugo=rwx /media/exthd

does nothing

---

### Post by LaurelLynn on 2007-04-12
Ok, 

What I am seeing looking at you /etc/fstab again is:

/dev/sdb1 /media/exthd auto users,atime,auto,rw,dev,noexec,suid 0 0

Two  things seem to be wrong with this.  With the ¨noexec¨ option you will not be able to run programs or scripts on the drive. Second is that the options include ¨users¨ and ¨auto¨.   Usually you see ¨auto¨ or ¨users,noauto¨.

The reason is that  auto mounts the drive at boot.  The only user active at mount it root, so user would just tell the os to mount the drive with root as the owner.  That would produce the symptoms you are seeing.

The ¨users¨ option allows anyone to mount or unmount the drive.  So you should be able to:

$ umount  /media/exthd
$ mount  /media/exthd

You should then own the drive and be able to do what you are trying to do with it.

The real problem is the FAT32 system I believe.  It has no file permissions of its own so one would think that anyone could write to it,  BUT if the drive mounts as ¨root¨ the whole drive belongs to ¨root¨ and nobody else can write to it.

As long as you have the FAT32 format,  write access belongs to whoever mounts it.

So either you can refomat it with a filesystem that has permissions such as ext2, ext3, etc... Which makes accessing it from windows difficult.

Or you can mount and unmount it when you need it.  If you want it to be there when you login, then you should mount it automatically everytime you log in.

The fstab entry becomes:

/dev/sdb1 /media/exthd auto users,atime,rw,dev,suid 0 0

So that root does not mount it at startup.  Then you edit the file ¨~/.bash_profile¨ and add to the end:

mount  /media/exthd

It should then be availabe when you log in, and then unmount when you log out.

---

### Post by nynoah on 2007-04-12
Ok here is how I fixed it to work.  I did not use the comand line.  I went into the systems settings, then to administrator then into the disk and file settings.  I then modified the people who could access it from Sudo to my ext...

Noah

---

### Post by LaurelLynn on 2007-04-12
That´s great! :D 

I´m just happy to know you got it working. ):P

---

### Post by nynoah on 2007-04-12
Thanks Laurellynn for helping me.  All you experienced users are great people for helping us lesser knowing newbies.   
Thanks again
Noah

---

