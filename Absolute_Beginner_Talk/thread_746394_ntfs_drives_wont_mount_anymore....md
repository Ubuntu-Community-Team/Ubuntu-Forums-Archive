---
title: "ntfs drives wont mount anymore..."
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by wcurtiss on 2008-04-05
hello all, new to the forums and to Ubuntu.  I have been installing ubuntu for a couple days now and finally got it all working the way it should.  I am dual booting with windows vista.  I installed KDE4 last night just to try it out and now I cant get my two ntfs drives to mount anymore.  when I click on the drives in Dolphin I get this error message.

org.freedesktop.hal.device.permissiondeniedbypolicy: hal-storage-fixed-mount-all-options refused uid 1002

I have done some research and I think it has something to do with policykit? and me not having the correct permissions to mount the drives, or something.  I have set permissions as high as I can in users & groups and that doesn't seem to matter.  Any help here would be greatly appreciated.  thanks.

---

### Post by jameswillmer on 2008-04-05
please post your 

/etc/fstab

file here

---

### Post by wcurtiss on 2008-04-05
so what, nobodies even gonna read it?  what happened to the much touted Linux support community?

---

### Post by wcurtiss on 2008-04-05
thanks for the reply.  here's the contents of my fstab file.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=cb0daeeb-37e7-4d89-92b9-d2f7b4b007d4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=ce04ad8f-ab53-4eff-8fe3-94ed7815a37c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

---

### Post by jameswillmer on 2008-04-05
ok you have 

hda1 = root file system
hda5 = swap

you don't have any entry in fstab for your ntfs partitions ....

[out of date howto deleted]

---

### Post by aaguilar4 on 2008-04-05
This might not be exactly what you're looking for, but I know that when Ubuntu (using Gnome) doesn't load up my windows partition (sda2) it's because i left it open (i.e. Windows is hibernating or on Suspend instead of correctly shutting it down).  
Just make sure that Vista is completely shut down and see if this helps.

---

### Post by jameswillmer on 2008-04-12
you need to add a line for your ntfs partition to the /etc/fstab file something like this

> UUID=6AA02170A02143C3 /media/winxp ntfs-3g defaults,locale=en_GB.utf8 0 0


Note that 

1) you need to find the UUID for YOUR hard disk not use mine.
> ls -l /dev/disk/by-uuid/

2) you might need to change locale for you

---

