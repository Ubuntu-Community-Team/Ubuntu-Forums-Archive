---
title: "NTFS drives locked"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by CalleKubuntu on 2005-12-30
Friends

I am trying to set up my dual-boot computer (XP Pro and Kubuntu) to do the following:

When booting into Kubuntu (Breezy), I would like for the Kubuntu to automatically mount the NTFS drives C, E and F, and do the same for the FAT32 drive G. 

Here are my fstab settings:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda8 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda1 /media/hda1 ntfs uid=0,gid=0,auto,ro,nouser 0 0
/dev/hda5 /media/hda5 ntfs uid=0,gid=0,auto,ro,nouser 0 0
/dev/hda6 /media/hda6 ntfs uid=0,gid=0,auto,ro,nouser 0 0
/dev/hda7 /media/hda7 vfat uid=0,gid=0,auto,rw,nouser 0 0
/dev/hda9 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

But now, whenever I start Kubuntu then the hda1, hda5 and hda6 are all locked. Those are the three Windows NTFS drives C,E and F. I can get into the hda7 (Windows G/FAT32) and read and write just fine. I have tried various settings in the fstab, but I always get the same results. If I go to the root / and then choose the /media folder, then I see all of the above ones, but all the ntfs ones are locked folders and I cannot access them. I should at least be able to read the contents of each partiton. What is wrong here?

Another related thing. 
If I go to the Konquerer and select Storage Media (ie media:/), then I come to an empty page . I don`t understand why it does not show me the stuff there. I mean, all the partiongs show up  when I manually first go to the root and then select the /media folder. Why not when I do it from Kongquerer/Storage Media??

Thanks for helping me understand what is going on.

CalleKubuntu

---

### Post by Suger on 2005-12-30
try changing to
[Snip]
/dev/hda1 /media/hda1 ntfs nls=utf8,umask=0222 0 0
/dev/hda5 /media/hda5 ntfs nls=utf8,umask=0222 0 0
/dev/hda6 /media/hda6 ntfs nls=utf8,umask=0222 0 0
[Snip]

This should do the trick.

By the way : I personnally find it easier to have the shared partitions in ext3 and to install this

[http://www.fs-driver.org/](http://www.fs-driver.org/)

in Windows (but in fact, I barely use Windows, only to load the iPod and to let my 2 years old son play with his wireless mouse, I can't get the game to work under wine up to now :( )

---

### Post by CalleKubuntu on 2005-12-30
[QUOTE=Suger]try changing to
[Snip]
/dev/hda1 /media/hda1 ntfs nls=utf8,umask=0222 0 0
/dev/hda5 /media/hda5 ntfs nls=utf8,umask=0222 0 0
/dev/hda6 /media/hda6 ntfs nls=utf8,umask=0222 0 0
[Snip]

This should do the trick.
888888888888888888888888888888888

Sorry Suger, but that did not change anything. I put what you suggested into the fstab and did a sudo mount -a then no change. 

If I go to /media and right-click on for example the icon for hda5, and choose Properties, I see the following:
Type: Locked Folder
...
Location: /media
Size: Could not neter folder /media/hda5

On the Permissions tab I see:
Owner can view content
Group forbidden
Others forbidden
User root
Group root

The only difference I see between the FAT32 and NTFS partitions in the /media is that the FAT32 (hda7) one has the file type folder, but the NTFS ones have file type Locked Folder. Well, the FAT32 one has the 
Owner can view and modfiy content 
and Group and Others can view content. 

I am confused. Please give me something else to try, will you. :(

---

### Post by CalleKubuntu on 2005-12-30
Hey, 

It worked, after all, but I had to reboot first. Thanks Suger.

I still am not clear why the partitions do not show up under Konquerer/Storage Media. Any clues?

Also, I notice that when I do a command "mount", then I see the following:

/dev/hda8 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=0222)
/dev/hda5 on /media/hda5 type ntfs (rw,nls=utf8,umask=0222)
/dev/hda6 on /media/hda6 type ntfs (rw,nls=utf8,umask=0222)
/dev/hda7 on /media/hda7 type vfat (rw,uid=0,gid=0)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)


Why are the ntfs partitions listed as rw, although I have the fstab setting as follows:
/dev/hda1 /media/hda1 ntfs nls=utf8,umask=0222 0 0
/dev/hda5 /media/hda5 ntfs nls=utf8,umask=0222 0 0
/dev/hda6 /media/hda6 ntfs nls=utf8,umask=0222 0 0

Is that umaks=0222 not telling the system to only allow read and not write?

Any ideas?

How can I get those icons for the mounted partitions to show up on the desktop? I remember them showing up automatically when using previous versions of Ubuntu/Kubuntu. 

Thanks for your help
CalleKubuntu

---

### Post by Suger on 2005-12-30
For the Konqueror part, I don't know, I don't have that much experience with KDE (I always run either gome or XFCE...), sorry.

For your mount -a problem, I guess you had forgotten to umount the faulty partitions before, no ?

For the ro/rw, are you sure you have write access on any of those partitions ? I don't think so.

For the icons, I know how to do it in Gnome (it's in Gconf, apps->nautilus->Desktop), but not in KDE, sorry.

---

