---
title: "[SOLVED] fstab ???"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-02
I have spent the last four hours trying to understand mounting and fstab. I am more confused now than when I started.

Here is what my system says I have.  /dev/sdb1, 5, and six are on the desktop at bootup. They show as V1, V2, and V3 icons. I can read, write make or delete anything in them.

They do not show up in fstab. How are they getting mounted???

I think I need to add them to fstab because when I do a backup with partimage it is a very confusing thing to get them mounted so the backup can be parked on one of them. 

What is the _exact_ entry for fstab to add these ??

Is there any other reason to add them to fstab?

=================================================
squrl@squrl-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G  4.7G  132G   4% /
varrun                506M   80K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  136K  9.9M   2% /proc/bus/usb
udev                   10M  136K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sdb1              25G  2.9G   22G  12% /media/V1
/dev/sdb5              26G   32K   26G   1% /media/V2
/dev/sdb6              25G  1.5G   23G   6% /media/V3

===================================================

squrl@squrl-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=26971987-3b36-4b6d-80af-9c8f78ed17bc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2f03bf5b-c2e2-42d4-998a-b0145181f099 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

=================================================

This is as much as I think I can ask right now brecause I don't know enough to ask more. This is only chapter one and when I feel I can comprehend more I'll continue.


Thanks to some intelligent soul.

---

### Post by ajgreeny on 2007-01-02
Have a look at this site.  I found it very useful.
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by bodhi.zazen on 2007-01-02
They are being mounted by gnome-volume-manager (gvm):

[http://gentoo-wiki.com/HOWTO_gnome-volume-manager](http://gentoo-wiki.com/HOWTO_gnome-volume-manager)
[http://www.linuxfromscratch.org/blfs/view/svn/gnome/gnome-volume-manager.html](http://www.linuxfromscratch.org/blfs/view/svn/gnome/gnome-volume-manager.html)

In general you do not use both gvm and fstab.

Mounting and permissions depends on the file system:

_Windows:_

[Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and umask=000[/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

Your fstab would look something like this:

/dev/sdb1 /mount_point auto defaults 0 0

You may need to adapt somewhat depending of what file system you are using.

HTH 8)

---

### Post by squrl on 2007-01-02
Thanks Gentlemen.  I read over the references and must admit I am not moxy enough to understand most of what was being said. I didn't try to enter or add anything to my system because I am not sure what may already be in place. 

I think I need to add to fstab enough to make using the rescue disk a little easier for iso backups.
My problem seems to be when having to mount the usb drive for a place to land the backup. Then again when restoring it. I have used the restore a couple times when I crewed up my system so bad there was no other way to recover and it sure beats trying to start over from scratch.

I think my system is in good shape and it's me not knowing what I'm doing that causes all my trouble :)  This was a lot easier back in my apple II days. Getting old is hell. :)

---

### Post by rccharles on 2007-01-02
> **squrl said:**
> 
Here is what my system says I have.  /dev/sdb1, 5, and six are on the desktop at bootup. They show as V1, V2, and V3 icons. I can read, write make or delete anything in them.

They do not show up in fstab. How are they getting mounted???



squrl@squrl-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=26971987-3b36-4b6d-80af-9c8f78ed17bc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2f03bf5b-c2e2-42d4-998a-b0145181f099 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

=================================================


Edgy used a different way of identifing the harddrive partitions.  See these two lines in fstab:

# /dev/sda1
UUID=26971987-3b36-4b6d-80af-9c8f78ed17bc /               ext3    defaults,errors=remount-ro 0       1

Edgy uses the UUID paramenter.  In this case, the UUID means /dev/sda1.  Edgy puts in the helpful comment to explain what the UUID means.

Seems obscure to me too.  I'd guess you can move devices around on your hardway and not have to chanage fstab.

Robert
:cool:

---

### Post by rccharles on 2007-01-02
> **squrl said:**
> 
I think I need to add to fstab enough to make using the rescue disk a little easier for iso backups.

I assume you are booting the system from your rescue disk.  When booting  a rescue disk, the fstab associated with the rescue disk will be the one used NOT the on on your harddrive.

Maybe this is confusing you when you do the rescue.  There is also the command mount which will tell you what partitions are mounted.

sudo mount

> **squrl said:**
> 
My problem seems to be when having to mount the usb drive for a place to land the backup. Then again when restoring it. I have used the restore a couple times when I crewed up my system so bad there was no other way to recover and it sure beats trying to start over from scratch.

I think my system is in good shape and it's me not knowing what I'm doing that causes all my trouble :)  This was a lot easier back in my apple II days. Getting old is hell. :)

perhaps you should look into some backup software.  

Robert

---

