---
title: "trying to rescue data on apple"
date: 2011-01-03
forum: Apple Hardware Users
---

### Post by lex1 on 2011-01-03
I have a volume that I am trying to recover data from due to a disk malfuncion

I am in a live cd 10.10 and need to know how to mount
Untitled 1 (apple disk)

I know how to mount it via the gui with the

gksudo nautilus command but I cannot move any of the data as it is owned by root in the apple permissions

So I plan to mount the volume via the command line then if possible
issue the commands


chown -R admin /path/to/folder
chmod u+rwX /path/to/folder 

admin being the apple user name

any ideas ?

lex1:guitar:

---

### Post by El Menda on 2011-01-03
Make a dir:

```
$ sudo mkdir /media/mac

```

Get all your partitions root:

```
$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2011-01-03 21:34 2860-11F4 -> ../../sda1
lrwxrwxrwx 1 root root 10 2011-01-03 21:34 2d364e8f-94e8-392e-a359-7436bde5cc78 -> ../../sda2
lrwxrwxrwx 1 root root 10 2011-01-03 21:34 c4a1aecc-d5ed-414c-b69f-73ba1fc81710 -> ../../sda4

```

Choose one and mount it:

```
$ sudo mount -t hfs /dev/sda2 /media/mac

```

If it's the partition you were looking for, then it's all done.
If not, umount it and choose another one:

```
$ sudo umount /media/mac

```

---

### Post by lex1 on 2011-01-03
thanks for your reply

here is what I get

ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2011-01-03 12:54 b57076ba-1686-3a1f-bc13-b9e4676987dd -> ../../sde1(this is a boot EFI hfs+ partition)
lrwxrwxrwx 1 root root 10 2011-01-03 12:54 d6e4cce5-7569-3f50-aab9-1d969733638e -> ../../sde2(this is the other hfs+ partition)

ubuntu@ubuntu:~$ sudo mount -t hfs /dev/sde1 /media/mac
mount: wrong fs type, bad option, bad superblock on /dev/sde1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -t hfs /dev/sde2 /media/mac
mount: wrong fs type, bad option, bad superblock on /dev/sde2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


seems they both will not monut?

lex1::guitar:

---

### Post by El Menda on 2011-01-03
Sorry, it's

```

$ sudo mount -t hfsplus /dev/sde2 /media/mac

```

---

### Post by lex1 on 2011-01-04
Thanks for your post


seems maybe my command might be incorrect?

ubuntu@ubuntu:/media/mac/Users$ ls
admin  Shared
ubuntu@ubuntu:/media/mac/Users$ cd
ubuntu@ubuntu:~$ sudo chown -R admin /media/mac/Users/admin
chown: invalid user: `admin'
ubuntu@ubuntu:~$ sudo chown -R admin /media/mac/Users/
chown: invalid user: `admin'
ubuntu@ubuntu:~$ 



lex1:guitar:

---

### Post by El Menda on 2011-01-04
Try better:

$ cd media/mac/Users/YourMacUserFolder
$ ls
And then seen the folders you want to recover, chmod then:
$ sudo chmod -R 777 Music

Now with Nautilus you can see that folder.

Note: don't use

---

### Post by lex1 on 2011-01-04
ok so you think 

u sudo chown -R admin:admin media/mac/Users/YourMacUserFolder

is not good 
but what you said is ok

lex1:guitar:

---

### Post by lex1 on 2011-01-04
chown: changing ownership of `/media/mac/Users/admin/Sites/.localized': Read-only file system
chown: changing ownership of `/media/mac/Users/admin/Sites/images/.DS_Store': Read-only file system
chown: changing ownership of `/media/mac/Users/admin/Sites/images/gradient.jpg': Read-only file system
chown: changing ownership of `/media/mac/Users/admin/Sites/images': Read-only file system
chown: changing ownership of `/media/mac/Users/admin/Sites/index.html': Read-only file system
chown: changing ownership of `/media/mac/Users/admin/Sites': Read-only file system
chown: changing ownership of `/media/mac/Users/admin': Read-only file system

its read only?

i saw this posted a while ago not sure if it still applies

[http://ubuntuforums.org/showthread.php?t=98286](http://ubuntuforums.org/showthread.php?t=98286)

lex1
:guitar:

---

### Post by El Menda on 2011-01-04
I forgot that if you didn't disable journaling from Mac OS, then you cannot write in that partition, just read.

What you can try it using a pendrive and copy all that important folders that you need. You can also upload that files to an FTP or a web service like Dropbox.

---

### Post by lex1 on 2011-01-04
Its to big for a pendrive and I have a linux remote server but even if i open a gui as root on the remote server and then with gksudo nautilus
on my ubuntu live cd I still do not have permission I tried to drag and drop but no look.

In the last post of the url I posted in the last post of this thread that I 
POSTED IT SAYS;
------------------------
Disabling journaling via diskutil

You can disable journaling from the Terminal application by using diskutil. Follow these steps:

1. Log in as an Admin user to the server whose disk you want to set up for journaling.
2. Make sure that no one is using the server.
3. Open Terminal (/Applications/Utilities/).
4. Execute the diskutil command, using the disableJournal option and identifying the volume for which you want journaling disabled. To disable journaling for the root volume, for example, you would execute:

sudo /usr/sbin/diskutil disableJournal /

To disable journaling for a volume called MyDisk, you would execute:

sudo /usr/sbin/diskutil disableJournal /Volumes/MyDisk 

------------------------------------------------------

but i am not sure about this

i could try

sudo /usr/sbin/diskutil disableJournal /Volumes/Unitiled 1

but remember Unitiled 1 is made up of two partitions 

sudo /usr/sbin/diskutil disableJournal /Volumes/sde2

but the post assumes you are inside the osx box not mounted not sure what the
outcome might be

lex1:guitar:

---

