---
title: "Cant mount hard drive"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Freddy The Cat on 2007-12-25
hello im a newb but what ever that really doesnt matter now does it?
ok to my problem i got no windows i accidentally  deleted it:( i know im dumb
i get this message when i try to mount my hard drive
[IMG]http://i255.photobucket.com/albums/hh138/FreddyTheCat/Screenshot-gnome-mount.png[/IMG]
so i tried choice 2 (both of them)
the comand line gave me this 

fred@Freds-Disapointment:~$ sudo mount -t ntfs-3g/dev/media/the other hard drive -o force
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
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

yeah i call it my disapointment cuz i lost windows!](*,)

then the fstab line it told me to do dont work
[IMG]http://i255.photobucket.com/albums/hh138/FreddyTheCat/Screenshot-gnome-mount-1.png[/IMG]
 i was thinking to try option 1 on another computer? maybe? i dunno
any help?

---

### Post by taurus on 2007-12-25
Try

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/hdb1
sudo mount -t ntfs-3g /dev/hdb1 /media/hdb1 -o force
df -h
```

---

### Post by Freddy The Cat on 2007-12-25
yeah! it works thnx!

---

### Post by csaga on 2007-12-27
When I installed the Feitsy Fawn, and want to access to my Windows NTFS drive, simple clicked in Nautilus with the drive name and put the password and everyting working fine, but I installed and uninstalled the NTFS configuration tools and the next reboot don't mount the NTFS drive! How can I obtain to mount the drive when was earlier?
Thanks for help!

---

### Post by taurus on 2007-12-27
> **csaga said:**
> When I installed the Feitsy Fawn, and want to access to my Windows NTFS drive, simple clicked in Nautilus with the drive name and put the password and everyting working fine, but I installed and uninstalled the NTFS configuration tools and the next reboot don't mount the NTFS drive! How can I obtain to mount the drive when was earlier?
Thanks for help!

Can you post

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

