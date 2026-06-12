---
title: "mounting NAS using nfs"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by myotis on 2008-04-13
Linked to an earlier post that no one can help me with.

I am trying to mount my NAS (QNAP 109 Pro)

I think I have made a mount point with:

sudo mkdir /media/public

I am then trying to mount the public share with:

sudo mount -t nfs 192.168.1.11:/public /mnt/public

But get an error:

/mnt/public does not exist

Have I missed out a step, or am I misunderstanding the instructions.

The directory /media/public exsits when I checked.

Thanks,

Graham

---

### Post by Helgiks on 2008-04-13
Try
sudo mount -t nfs 192.168.1.11:/folder you want to mount/ /media/public

like sudo mount -t nfs 192.168.1.11:/home/$USER/public/ /media/public

where /home/$USER/public is on 192.168.1.11.

---

### Post by sisco311 on 2008-04-13
```
 sudo mount -t nfs 192.168.1.11:/public /mnt/public
```you try to mount the partition in /mnt/public not in /media/public

```
 sudo mount -t nfs 192.168.1.11:/public **/media/public**
```

---

### Post by myotis on 2008-04-13
Thanks to you both,

I tried:

sudo mount -t nfs 192.168.1.11:/public /media/public

as that seemed the simplest starting point, but get an error

mount: wrong fs type, bad option, bad superblock on 192.168.1.11:/public,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I assume this refers to the "nfs" bit, but this is what the QNap instructions say for mounting the NAS on linux.

Graham

---

### Post by myotis on 2008-04-13
To reply ro myself it looks as if I need to install from programs to make nfs work, so I will give that a go.

[http://ubuntuforums.org/showthread.php?t=688250](http://ubuntuforums.org/showthread.php?t=688250)

Graham

---

### Post by myotis on 2008-04-13
Based on the link in the last email, I have now run these commands

sudo apt-get install util-linux
 sudo apt-get install portmap
sudo apt-get install nfs-common

And get the following when I try to mount the NAS

graham@Antec-Linux:~$ sudo mount -t nfs 192.168.1.11:/public /media/public
mount.nfs: mount to NFS server '192.168.1.11' failed: System Error: Connection refused

I then ran

sudo /var/lib/dpkg/info/nfs-common.postinst

Then

sudo aptitude update
sudo aptitude safe-upgrade
sudo dpkg-reconfigure nfs-common
sudo aptitude reinstall nfs-common


Still getting the same error

Graham

---

### Post by myotis on 2008-04-15
As the help seems to have dried up here, I am going to move this the networking forum.

Thanks to those who have tried to help.

Graham

---

