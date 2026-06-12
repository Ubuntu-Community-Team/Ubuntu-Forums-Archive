---
title: "Virtual CD-Rom"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by handband2 on 2006-02-10
Does anyone know a way or a website that gives Ubuntu the ability to create a virtual cd-rom?  Because I have .iso's and rather than burning the cd I rather just mount them to install the software.

Thanks!

---

### Post by lha on 2006-02-10
Use
```
mkdir fakecd
sudo mount cd.iso fakecd -o loop
```
where cd.iso is your cd image and fakecd the directory where you want your 'virtual cd' be.

---

### Post by nixclusive on 2006-02-10
If the above fails...:

```

sudo modprobe loop
sudo mount /<path_to_iso> /<mount_point> -t iso9660 -o loop

```

---

### Post by handband2 on 2006-02-10
lha,

Thanks!  It worked so now how to you switch it back to the cd.iso file?

---

### Post by ebash on 2006-02-10
Use :
umount  /<mount_point>

---

### Post by handband2 on 2006-02-10
Thanks!

I also used this and it seemed to work...

sudo umount /location -l

---

### Post by Soccarrfreak on 2006-02-14
Hey, I have some DVD .iso's and would like to mount them to a "virtual drive".  I created /vcd (virtual cd) but when i try to mount the iso there it gives me this:

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

Also if i get this to work with your help, how will i have it "launch" it as cd/dvd?

---

### Post by lha on 2006-02-14
[QUOTE=Soccarrfreak]Hey, I have some DVD .iso's and would like to mount them to a "virtual drive".  I created /vcd (virtual cd) but when i try to mount the iso there it gives me this:

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

Also if i get this to work with your help, how will i have it "launch" it as cd/dvd?[/QUOTE]
What command you tried to use to mount that iso?

If 'how to launch' means 'how to watch that dvd', open Totem and tell it to open dvd's mount point. Maybe you'd be interested in Ogle. It is able to play dvd-isos directly, so you wouldn't need to mount them first.

---

### Post by GreyFox503 on 2006-02-14
Yes, that error means that the syntax of the command you entered was incorrect.  Please copy & paste the exact command here for us.

---

### Post by george_apan on 2006-02-14
There is a HOWTO with a couple of nautilus scripts to mount .iso files. Here:
[http://ubuntuforums.org/showthread.php?t=87369](http://ubuntuforums.org/showthread.php?t=87369)

I use them and they work fine.

---

### Post by arjunsharma on 2006-02-24
what if I have a .mds file? How can I mount that?

Thanks,

Arjun

---

### Post by george_apan on 2006-02-27
As far as I can remember an .mds file is just an md5 checksum file for an .iso file. So along with the .mds file there should be an .iso. An .mds file does not contain any data at all. So you could mount the .iso file anyway.

---

### Post by madjr on 2008-03-29
you can also mount isos with a gui using **gmount-iso** (in the repos or add/remove)

theres also:
[http://www.acetoneiso.netsons.org/viewpage.php?page_id=2](http://www.acetoneiso.netsons.org/viewpage.php?page_id=2)

---

### Post by bulletxt on 2008-03-29
as AcetoneISO supports all images, I suggest you to use it

---

