---
title: "mounting mybook issue"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by mentalpuff on 2008-01-19
hi. im fairly new to ubuntu, its been an up and down experience in the past and i usually end up going back to windows because i never had the time to learn all these things. eventually i reached my frustration level with that system, and decided i'd make the time to learn. i need some help here getting everything the way i want it to be, and i've looked around at all the posts and some helped and didnt help, i have a lot of things that need to get tweaked eventually but i figure i'll start out slow, with the most important things, and eventually get everything set up slowly over the days. getting to my problem.
i have an external WD mybook drive, 500 gigs. before switching i backed up all the things i wanted to bring along with me on this drive. i did it with an ntfs file system so i wouldnt get  limited, it has around 400 gigs full of stuff. anyway
i try to access it in ubuntu. and a mountin error comes up. I'll hafta type it out since i cant copy and paste it.

cannot mount volume, unable to mount the volume 'External One'.
Details>
$LogFile indicates unclean shutdown(0,0) Failed to mount '/
dev/sdc1': Operation not supported Mount is denied
because NTFS is marked to be in use. Choose one action:
Choice 1: if you have windows then disconnect the external 
devices by clicking on the "Safely Remove Hardware"
icon in the windows taskbar then shutdown windows cleanly. 
Choice 2: if you dont have windows then you can use the 'force'
option for your own responsibility. for example type on the commandline:
mount-t ntfs-3g/dev/sdc1/media/External One -o force  Or add
the option to the relevant row in the /etc/fstab file: 
/dev/sdc1/media/External One ntfs-3g defaults,force 0 0

I didnt have windows anymore, so i went with the command line option first.
I went in and put  mount -t ntfs-3g/dev/sdc1/media/External One -o force and that
brought up a list of things which looked like mounting commands:

root@bew:/home/bew#  mount -t ntfs-3g/dev/sdc1/media/External One -o force
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

since that didnt seem to do anything, i went to /etc and opened up my fstab file. I tried to enter "/dev/sdc1/media/External One ntfs-3g defaults, force 0 0" to the bottom of the file and save it, but it wouldnt let me save it because "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."
The drive uses a usb 2.0 interface, as well as esata. I used the esata interface on windows, and switched it to usb when i thought that was the issue. Does ubuntu natively support esata?
Sorry for the lengthy post, but I like this OS, i just wanna make it work for me. Any suggestions would be more than appreciated.
-Bew

---

### Post by gn2 on 2008-01-19
To save the file you would need the required user priviledges.

One easy way of doing so is to press Alt+F2 then type
```
gksudo nautilus
```
[COLOR="Red"]This will give you full administrative (root) priviledges to alter all vital system files so go carefully![/COLOR]

Navigate to the file you want to edit and the changes will be saved.
Close the file browser as soon as you're finished ;-)

Another difficulty could be the WD Mybook's restrictive firmware, have you checked the WD site to confirm it's Linux compatibility?

---

### Post by mentalpuff on 2008-01-19
thankyou. that helped with saving the file, but..
i added what the error report said to add, and it didn't do anything. here's a copy of my fstab file:

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=24575c9f-4bd2-4809-a519-ec22ba56d522 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=EA2041B520418991 /media/sda1 ntfs-3g defaults,locale=en_CA.UTF-8 0 1
# Entry for /dev/sda3 :
UUID=4a1747f6-7ef9-4506-b67f-54ead62b9a28 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
/dev/sdc1/media/External One ntfs-3g defaults,force 0 0

as you can see, i added it to the bottom. it said to add to the relevant row which im not sure where that is. the same error came up, but im at least taking notes.

-bew

---

### Post by mentalpuff on 2008-01-19
hi. i wasn't able to fix this issue through ubuntu, rather i looked for a laptop that had windows on it, connected it, and chose the safely remove hardware option. then i disconnected it, turned it off, then reconnected it to my linux box and it worked. just thought id say so incase it helps anyone else.

---

