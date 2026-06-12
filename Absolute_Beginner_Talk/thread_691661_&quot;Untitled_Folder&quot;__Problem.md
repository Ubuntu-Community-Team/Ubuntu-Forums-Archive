---
title: "&quot;Untitled Folder&quot;  Problem"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by usater on 2008-02-08
hai, friends

i'm using gusty(7.10)

my problem is that i cannot copy a file or create a directory in my home folder

i used to dnld 700mb or (around that) files and try to extract it.

i'm using a 4.5gb partition for /home . system noting 3.3gb free when this problem occure.

My browsers are firfox n opera.

when this problem occur i cannot login after a reboot as some error message saying that "cannot write to home directory. user sould have 644 permission on /home "

if i entered command prompt n delete something the problem get solved. but it repeat regularly.

i noted that all the problems occurred after installing wine. so i used to uninstall it if this occur.

but later i noted it's occurring without wine too.....??

Please help 

Thanks in advance

---

### Post by spiderbatdad on 2008-02-08
could you post /etc/fstab?

---

### Post by usater on 2008-02-08
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=e2c62ed6-e628-45c6-aef2-354ace4addf9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=047d81a5-75e8-47c9-968d-17a51d93f5fe /home           ext3    defaults        0       2
# /dev/sda1
UUID=6C18820D1881D68C /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda10
UUID=842C9D132C9D00FA /media/sda10    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=8A04663804662801 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda9
UUID=44FA-BCDF  /media/sda9     vfat    defaults,umask=007,gid=46 0       1
# /dev/sda8
UUID=455ec33b-792a-4bcd-9304-c6cd963be36b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by usater on 2008-02-09
plesae help

This problem repeat after extracting big archives

I got This message on login

-------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------
(process:5148): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5152): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/workshop:/tmp/.ICE-unix/5145
Window manager warning: Failed to read saved session file /home/net/.metacity/sessions/default0.ms: Failed to open file '/home/net/.metacity/sessions/default0.ms': No such file or directory


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
** Message: Not starting remote desktop server

** (update-notifier:5216): WARNING **: not starting because user is not in admin group

Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
Initializing gnome-mount extension
evolution-alarm-notify-Message: Setting timeout for 64978 1202601600 1202536622
evolution-alarm-notify-Message:  Sun Feb 10 05:30:00 2008

evolution-alarm-notify-Message:  Sat Feb  9 11:27:02 2008


(gnome-panel:5197): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24
[NoScript] [NoScript] browserDOMWindow wrapped for external load interception

------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------

help

---

### Post by spiderbatdad on 2008-02-09
i believe the problem is with the umask values...set to umask=000, or umask=022, but you may want to wait for an expert opinion.

---

### Post by usater on 2008-02-09
but sda 1,sda 5,sda10 are ntfs partitions so what can be the problem with the umask value?

sda 9 is vfat

sda 6 ==> /                   (ext3)

sda 7 ==> /home          (ext3)

---

### Post by spiderbatdad on 2008-02-10
there is a program available called disk manager, purported to make mounting file systems an easy task for regular users. There is a wiki topic here.[https://wiki.ubuntu.com/DiskManagerByDefault](https://wiki.ubuntu.com/DiskManagerByDefault)

It can be downloaded here:[http://flomertens.free.fr/disk-manager/download.html](http://flomertens.free.fr/disk-manager/download.html)

The edgy is supposed to install fine on gutsy...if you try to build from source, I believe you will have to install dmsetup first.

---

