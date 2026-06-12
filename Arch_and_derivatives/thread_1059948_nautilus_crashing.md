---
title: "nautilus crashing"
date: 2009-02-04
forum: Arch and derivatives
---

### Post by stonecoldjha on 2009-02-04
i got gnome-session finally working on arch.But,when i click on places>computer,a window called bug buddy comes up asking me to submit bug report,prompting me for my email,etc.The following are the crash details:

Distribution: Unknown
Gnome Release: 2.24.3 2009-01-20 (Archlinux)
BugBuddy Version: 2.24.2

System: Linux 2.6.28-ARCH #1 SMP PREEMPT Sun Jan 25 10:13:11 UTC 2009 i686
X Vendor: The X.Org Foundation
X Vendor Release: 10503000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Clearlooks
Icon Theme: gnome

Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

i can't open "computer".please help.

---

### Post by smartboyathome on 2009-02-04
Run Nautilus in a terminal and post the output when it crashes.

---

### Post by stonecoldjha on 2009-02-04
Please see the screenshot.

---

### Post by stonecoldjha on 2009-02-04
as you can see the terminal output was follows:

[sonujha@arch ~]$ nautilus

(nautilus:2041): GVFS-RemoteVolumeMonitor-WARNING **: remote volume monitor with dbus name org.gtk.Private.HalVolumeMonitor is not supported

(nautilus:2041): GVFS-RemoteVolumeMonitor-WARNING **: remote volume monitor with dbus name org.gtk.Private.GPhoto2VolumeMonitor is not supported

** (nautilus:2041): WARNING **: Cannot connect to DBus Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

process 2041: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3298.
This is normally a bug in some application using the D-Bus library.
  D-Bus not built with -rdynamic so unable to print a backtrace
24859997-ed49-d909-4d8b7a9e-37a32393 is dumped

(bug-buddy:2045): libebook-WARNING **: e_book_construct: Could not obtain a handle to the Personal Addressbook Server with IID `OAFIID:GNOME_Evolution_Exchange_Connector_BookFactory:1.2'

[sonujha@arch ~]$

---

### Post by smartboyathome on 2009-02-04
Looks like it is crashing because dbus isn't started. Have you run "sudo /etc/rc.d/hal start"?

---

### Post by stonecoldjha on 2009-02-04
yeah..........after doing #/etc/rc.d/hal start  nautilus started working.thanks for that.
but,will i have to do this everytime i boot up?can't i do something so that it is invoked on its own?

---

### Post by stonecoldjha on 2009-02-04
one more thing,i tried opening my partitions,but they didn't saying that i didn't have permissions to mount them.how do i solve this?

---

### Post by SkonesMickLoud on 2009-02-04
> **stonecoldjha said:**
> yeah..........after doing #/etc/rc.d/hal start  nautilus started working.thanks for that.
but,will i have to do this everytime i boot up?can't i do something so that it is invoked on its own?

Add hal to your daemons array in /etc/rc.conf:

```
DAEMONS=(... @hal ...)
```

The @ backgrounds the start of hal, lowering boot times.

> **stonecoldjha said:**
> one more thing,i tried opening my partitions,but they didn't saying that i didn't have permissions to mount them.how do i solve this?

You have to have root permissions to mount volumes.  Whether you do this as root, or with sudo is up to you.

---

### Post by stonecoldjha on 2009-02-04
but in ubuntu i can easily mount my partitions.i want it to be so.is that not possible?

---

### Post by stonecoldjha on 2009-02-04
i want all partitions to be mounted,so that i can use them once i double-click them.

---

### Post by SkonesMickLoud on 2009-02-04
> **stonecoldjha said:**
> i want all partitions to be mounted,so that i can use them once i double-click them.

Add them to /etc/fstab.

---

### Post by stonecoldjha on 2009-02-04
as you can see all the partitions are there in my /etc/fstab:

# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0


#/dev/cdrom /media/cdrom   auto    ro,user,noauto,unhide   0      0
#/dev/dvd /media/dvd   auto    ro,user,noauto,unhide   0      0
UUID=26c0405d-1389-4c95-af30-348bf932e930 swap swap defaults 0 0
UUID=8fb2110a-e5f9-4185-bdbc-cfcf12bff661 / ext3 
defaults,noatime,noadiratime 0 1
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda1                                  /media/sda1    ntfs         nls=iso8859-1,umask=000     0  0  
/dev/sda5                                  /media/sda5    ext3         errors=remount-ro           0  0  
/dev/sda6                                  /media/sda6    ext3         errors=remount-ro           0  1 
/dev/sda7                                  /media/sda7    ext3         errors=remount-ro           0  0  
/dev/sda8                                  /media/sda8    swap         sw                          0  0

---

### Post by mips on 2009-02-04
stonecoldjha,

I'm really not trying to be funny or anything but could I suggest you go through all the steps in the beginners guide again. You really should not have as many problems as you are experiencing. If you follow the guide to the letter you will be a-ok :)

---

### Post by stonecoldjha on 2009-02-04
i could solve all the problems i encountered so far.now,there remains only one,and that is making my partitions automount when i log in as a non-root user.please,this is the last problem i suppose

---

### Post by SkonesMickLoud on 2009-02-04
> **stonecoldjha said:**
> i could solve all the problems i encountered so far.now,there remains only one,and that is making my partitions automount when i log in as a non-root user.please,this is the last problem i suppose

Try putting "user" or "auto" under the options column.

Auto will automatically mount said partitions at boot.  User will allow any user to manually mount said partitions without root or sudo access.

---

### Post by stonecoldjha on 2009-02-04
even this did not work.

i double-clicked on my 31.5 GB NTFS partition,and it did not mount,but,when i clicked "details",it said that the mountpoint /media/sda1 did not exist.likewise,the mount points of all other partitions do not exist as per the details i get on trying to open them.

---

### Post by stonecoldjha on 2009-02-04
even the terminal output reveals that:

[sonujha@arch ~]$ sudo mount /media/sda1
Password: 
mount: mount point /media/sda1 does not exist
[sonujha@arch ~]$

but,i have the same mount points existing for my ubuntu installation(in fact i copied the contents off the fstab of ubuntu into the fstab of arch expecting to automount).now,how do i change mountpoints and how?

---

### Post by SkonesMickLoud on 2009-02-04
> **stonecoldjha said:**
> even the terminal output reveals that:

[sonujha@arch ~]$ sudo mount /media/sda1
Password: 
mount: mount point /media/sda1 does not exist
[sonujha@arch ~]$

but,i have the same mount points existing for my ubuntu installation(in fact i copied the contents off the fstab of ubuntu into the fstab of arch expecting to automount).now,how do i change mountpoints and how?

You have to make those mount points.  Remember that Arch isn't Ubuntu.  It's not going to do all of the "work" for you.

At your command line:

```
mkdir /media/sda1
```

Repeat this for all of the filesystems you want to mount.

Your mount command is also wrong.  Should read something like this:

```
mount -t <filesystem type> /dev/sda1 /media/sda1
```

You will have to make all of the mountpoints by hand, but you should only need to manually mount the filesystems once.  Adding "auto" to /etc/fstab should take care of that in the future.

---

### Post by stonecoldjha on 2009-02-05
thanks,now it works after i created the mountpoints.thank you,very much.

---

