---
title: "[SOLVED] manipulator app"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-13
Can anyone tell me if there is an app for ubuntu to manipulate files folders and permissions that uses a gui. 

Thanks

---

### Post by taurus on 2007-01-13
Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by jem7v on 2007-01-13
Yeah, all you have to do is right-click on the object you want to set permissions for and choose Properties, then go to the Permissions tab.  You might not need to run it with gksudo, though, depending on what folders you want to set permissions on.  (If it's something in your own home folder, you probably won't need to.)  Nautilus, by the way, is just the file browser.  You can also get to it by going Places->(Computer or Desktop or Home Folder).

---

### Post by squrl on 2007-01-13
What does this mean ??

squrl@squrl-desktop:~$ gksudo nautilus
(nautilus:6053): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by taurus on 2007-01-13
Just a warning.  Nautilus window still opens right?

---

### Post by squrl on 2007-01-13
A file window opened but didn't look any different than before. I'll try again

---

### Post by taurus on 2007-01-13
> **squrl said:**
> A file window opened but didn't look any different than before. I'll try again

What do you mean it didn't look any different than before?  Navigate around with it and if you want to change a permission of something, right click on the icon and go to Properties and change it from there.  Be careful, you are running nautilus as root right now...

---

### Post by squrl on 2007-01-13
If thats the case why is the button for changing owners and permissions grayed out. 

Ive been to the right click thing many times to check permissions and ownership but have never been able to change anything. Nautilus doesn't show up anywhere in the applications or system menu's. Maybe it really isn't there :)   "please mighty one give me back dos"

---

### Post by taurus on 2007-01-13
Are you trying to change permissions on ntfs or fat32 filesystem?

---

### Post by squrl on 2007-01-13
No. I don't have any ntfs anymore. This is on the usb drive that appears on the desktop. It is a ext3 partition.

Also in this nautilus thing. When I select a file that I want to move or open and it belongs to root and I right click on it then go to permissions and make achange there it wont stick. How do you make permanent changes in this nautilus?

---

### Post by taurus on 2007-01-13
What's why you want to run "gksudo nautilus".  Then, you can move, change, delete, etc. anything you want.

---

### Post by squrl on 2007-01-13
except that nautilus wont run on the other drive. Probably because its not mounted in fstab huh?

How is it getting mounted?

Thanks Taurus I have almost had enough fun for this year.  Maybe its time to find a new irritation. :)

I looked into classes at UMKC and a couple other colleges in town but they won't let you in even to audit them if you aren't in a degree program. 

I got irritated and threatened them as a tax payer for the last 60 years and now they are reconsidering my request.

---

### Post by taurus on 2007-01-13
What's the output of this command from a terminal (and may as well include your /etc/fstab too)?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by squrl on 2007-01-13
squrl@squrl-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23944   192330148+  83  Linux
/dev/sdb2           23945       24321     3028252+   5  Extended
/dev/sdb5           23945       24321     3028221   82  Linux swap / Solaris


squrl@squrl-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b34ea331-60f2-4351-8a61-6d50535b7cd7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b8f4fba9-4544-423b-9d04-7bb239811156 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
squrl@squrl-desktop:~$

---

### Post by taurus on 2007-01-13
Looks to me like you have two versions of Linux on your machine, one on master drive and other on the slave drive!  Do you use (boot) both of them or you only use one exclusively?  Right now, you use the version on the master drive so I guess you want to mount the one on the slave drive so you can access stuff from it, yes?

```
gksudo gedit /etc/fstab
```
Then add these two lines to the end of it.

```

/dev/sdb1   /media/sdb1   ext3   defaults   0   1
/dev/sdb5   none   swap   sw   0   0
```
Save it.  Then, create a new mount point for it and mount it (and the swap partition as well).

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
free
```

---

### Post by squrl on 2007-01-13
squrl@squrl-desktop:~$ gksudo gedit /etc/fstab
(gedit:10275): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
squrl@squrl-desktop:~$ sudo mkdir /media/sdb1
squrl@squrl-desktop:~$ sudo mount -a
squrl@squrl-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G  7.2G  130G   6% /
varrun                506M   80K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  128K  9.9M   2% /proc/bus/usb
udev                   10M  128K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sdb1             181G  4.8G  167G   3% /media/usbdisk
/dev/sdb1             181G  4.8G  167G   3% /media/sdb1
squrl@squrl-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1035136    1004632      30504          0      10360     835008
-/+ buffers/cache:     159264     875872
Swap:      3028212      17656    3010556
squrl@squrl-desktop:~$ 


I have the main OS on the hard drive that I use but also have another installed on the usb drive. I can boot from either by selecting at startup. 

Thanks for the help. Maybe I'm trying to soak up to much to fast. This really shouldn't be this hard. Between age and the learning curve it gets a little trying. At least my mind is active even if the rest isn't :)

---

### Post by taurus on 2007-01-13
I see that /dev/sdb is your USB drive because the automount already mounted it to /dev/usbdisk.  Therefore, you don't have to mount /dev/sdb1 to /media/sdb1 if you don't want to.  ;)

---

