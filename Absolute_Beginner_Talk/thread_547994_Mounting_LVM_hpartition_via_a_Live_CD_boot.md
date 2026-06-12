---
title: "Mounting LVM hpartition via a Live CD boot"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Tatty on 2007-09-10
Hi all,

My laptop is dead.  Some sort of hardware failure, which has corrupted my hard disk so its going back to be repaired,  But first i want to rescue my /home directory.

I can only boot off a live CD, but when i tried using the mount command i got :

```
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda5 /test
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I am using an LVM partition, which according to the gnome partition manager is known as /dev/sda2, with the main partition i am after as /dev/sda5

Is this error caused because i am trying to mount an LVM partition?  I have tried changing ext3 to LVM, but 'mount' does not recognise lvm as a filesystem.

I tried looking for specific lvm commands in the terminal - i remembered coming across them before, but did not play with them too much - but it appears they arent installed, so i tried installing lvm-common (it sounded like the right kind of thing in the description in synaptic) but got this error:

```
ubuntu@ubuntu:~$ sudo apt-get install lvm-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  lvm-common
0 upgraded, 1 newly installed, 0 to remove and 77 not upgraded.
Need to get 0B/17.3kB of archives.
After unpacking 156kB of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 13213 package `x11-common':
 `Conflicts' field, invalid package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

so now i am really stuck... :confused:

---

### Post by Tatty on 2007-09-10
cheeky bump before it disappears into the dreaded second page :popcorn:

---

