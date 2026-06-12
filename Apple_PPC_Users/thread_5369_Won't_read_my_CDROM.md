---
title: "Won't read my CDROM"
date: 2004-11-18
forum: Apple PPC Users
---

### Post by franx on 2004-11-18
Dumb question, I know, but how do I get Ubuntu to see and run my CDROM drive?  So far nothing will read my CDs.

---

### Post by dataw0lf on 2004-11-18
Is there anything in /media/cdrom0? Otherwise,  display your /etc/fstab in here, as well as trying to mount it manually, ie mount -t iso9660 -o ro /dev/<fill in with appropriate hd, usually hdd or hdc> /cdrom
dataw0lf

---

### Post by franx on 2004-11-18
My cdrom device is /dev/hdb with mount-point /media/cdrom.  I've tried a bunch of variations on the following (in root):

# mount -t iso9660 /dev/hdb /mnt

and

# mount -t iso9660 /dev/hdb /media/cdrom /mnt

etc.

Nothing is working.  Any ideas?

---

### Post by ktindle on 2004-11-19
What kind of machine is this?  The hdb implies that the drive is an ATAPI connected as
a primary slave.  Is this in fact how the drive is connected and jumpered?  Some Mac
I/O interfaces do not like ATAPI and hard disk drives connected on the same ribbon.

Make sure that /sys/block/hdb is available if you have a 2.6 series kernel.
The ide-cd module must be loaded, so

lsmod | grep ide_cd

should show this.

---

### Post by oakz on 2004-11-19
Does the mount point exist? Make sure that the /media/cdrom directory exists.
Also, I did not see this listed in your comments, did you try the following as root (as suggested by dataw0lf):

$ mount -t iso9660 /dev/hdb /media/cdrom

Also, are you sure hdb is your CD drive? /dev/cdrom is usually automatically configured at installation time to point at you CD device, so also give this a try:

$ mount -t iso9660 /dev/cdrom /media/cdrom

Are you also sure that the CD is not already mounted automatically at /mnt/cdrom (which is the usual mount point I have seen in Linux systems) or somewhere else?

Execute "mount" without any arguments to see if /dev/cdrom or /dev/hdb is already mounted.

---

### Post by eggie on 2004-11-26
[QUOTE=oakz]Does the mount point exist? Make sure that the /media/cdrom directory exists.
Also, I did not see this listed in your comments, did you try the following as root (as suggested by dataw0lf):

$ mount -t iso9660 /dev/hdb /media/cdrom

Also, are you sure hdb is your CD drive? /dev/cdrom is usually automatically configured at installation time to point at you CD device, so also give this a try:

$ mount -t iso9660 /dev/cdrom /media/cdrom

Are you also sure that the CD is not already mounted automatically at /mnt/cdrom (which is the usual mount point I have seen in Linux systems) or somewhere else?

Execute "mount" without any arguments to see if /dev/cdrom or /dev/hdb is already mounted.[/QUOTE]
 Same problem here  --unable to mount cd to desktop to access my gigs of music

---

### Post by slux on 2004-11-27
What's the exact error message? What do you get from "dmesg | grep hdb"?

---

### Post by Fidtis on 2008-01-07
Hello,

I'm having the same problem with my CD-ROM player, however, my powerbook doesn't even see the player.  I can't even open it up.  I upgraded from Feisty (the cdrom/dvd player worked great) to Gutsy the other day and all is well except for my player.  Here is some info on my machine:

uname -a
Linux G3 2.6.22-14-powerpc #1 Tue Dec 18 08:48:38 UTC 2007 ppc GNU/Linux

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=2c90fa74-f137-474c-a307-1ecf7b3002c0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=c13724dd-3fc3-4389-8982-3c6c3285e6f3 none            swap    sw              0       0
/dev/hde        /media/cdrom0   udf,iso9660 user,noauto     0       0

sudo mount -t iso9660 /dev/hde /media/cdrom0
mount: special device /dev/hde does not exist

Do I need to create a device?  Any suggestions anyone may have would be greatly appreciated.

Thanks

---

