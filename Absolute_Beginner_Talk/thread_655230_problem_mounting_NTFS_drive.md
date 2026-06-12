---
title: "problem mounting NTFS drive"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by umarali on 2008-01-01
i have two hard-drives in my pc
one with windows installed [3 partitions]
and the other one with ubuntu [ single partition].
i had installed ubuntu just to see what its like and stuff and now prefers it over windows. just recently i updated to gutsy gibbon and now it would only mount the drive with Ubuntu on it and only the "C drive" from the other ones. if i try to open the other ones it gives me a  huge error message. i couldnt copy the stuff on it so i took a screen shot: 
[IMG]http://img88.imageshack.us/img88/9752/screenshotgnomemountne5.png[/IMG]

PLEASE HELP :(

---

### Post by BL00dFox on 2008-01-01
Do what it says; you pulled the drive out before safely removing it on a windows machine. Or, you can always try the "choice two" on the error message.

---

### Post by kestrel1 on 2008-01-01
I had a similar problem with a USB HDD. I re-booted in to windoze & safely removed the drive, then rebooted to Ubuntu. Problem solved.
If this is a fixed drive, I would run checkdisk (chkdsk) on it from Windoze.

---

### Post by umarali on 2008-01-02
its a fixed drive :(
i tried option two. this is what i get:
> Usage: mount -V                 : print version
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
For many more details, say  man 8 mount 

i dont get it....im really new to ubuntu
:(

edition: just now i also tried modifying the /etc/fstab file and i get an error saying that i do not have the permissions to make these changes....but....i am the admin!!! :confused: :confused:

---

### Post by kestrel1 on 2008-01-02
To edit the fstab file you need to type:
```
sudo gedit /etc/fstab
```

By the look of your post, you only typed in mount. You need to type mount /dev/hda1 (hda1 being partition 1 on drive hda) If it is SATA or SCSI I think it would be sda1)

---

### Post by umarali on 2008-01-03
what the hell!! it doesnt even show the other two drives anymore!!!!
i tried editing the file anyways but no good :(:(:confused::confused:

---

### Post by kestrel1 on 2008-01-03
If you go to System - Administration - System Monitor & click on the File Systems tab what do you see?

---

### Post by eternicode on 2008-01-03
If you haven't already, I would strongly suggest booting into windows, rebooting into windows again, then boot into Ubuntu, and see if it's fixed.

When booting into windows, if an automatic checkdisk pops up, let it work.

---

### Post by umarali on 2008-01-05
i SOMEHOW managed to get the other drives to work...but there is still one that wouldnt mount.
it give the same error message
any suggestions?
:confused:

---

### Post by umarali on 2008-01-05
btw:
> **kestrel1 said:**
> 
By the look of your post, you only typed in mount. You need to type mount /dev/hda1 (hda1 being partition 1 on drive hda) If it is SATA or SCSI I think it would be sda1)

this is what i typed in:
```
sudo mount -t ntfs-3g/dev/hda5/media/For All -o force
```

For All = name of partition :P

---

### Post by thamood on 2008-01-05
boot into windows....and do a drive check to clean the errors and then boot into ubuntu again it should work....

---

### Post by zasf on 2008-01-05
> **umarali said:**
> i have two hard-drives in my pc
one with windows installed [3 partitions]
and the other one with ubuntu [ single partition].
i had installed ubuntu just to see what its like and stuff and now prefers it over windows. just recently i updated to gutsy gibbon and now it would only mount the drive with Ubuntu on it and only the "C drive" from the other ones. if i try to open the other ones it gives me a  huge error message. i couldnt copy the stuff on it so i took a screen shot: 
[IMG]http://img88.imageshack.us/img88/9752/screenshotgnomemountne5.png[/IMG]

PLEASE HELP :(

try

```
sudo mount /dev/hda5 /media/For\ All -o force
```

sometimes I also have to force my windows drive to mount.

Matteo

PS: you might also not want to use spaces in directory names

---

### Post by kestrel1 on 2008-01-05
Have you got a space in the partition name? If so I think you need to enclose it in speach marks, so it would look like this:
```
sudo mount -t ntfs-3g/dev/hda5/media/"For All" -o force
```

---

### Post by umarali on 2008-01-16
like i said earlier...this is what i get when i type the above code in terminal...
> Usage: mount -V : print version
mount -h : print this help
mount : list mounted filesystems
mount -l : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
mount -a [-t|-O] ... : mount all stuff from /etc/fstab
mount device : mount device at the known place
mount directory : mount known device here
mount -t type dev dir : ordinary mount command
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
or by label, using -L label or by uuid, using -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say man 8 mount

and btw... as far as booting into windows is concerned....i cant do that :(....ive got this weird problem with it that when i try to boot it...when its loading  (the xp logo with the progress bar thingy under it) my pc restarts :S:oops:....i dunno if thats the doing of a virus or a hardware problem... :(

---

### Post by zasf on 2008-01-16
please, past here not only the output but also the exact command that you're entering

---

### Post by umarali on 2008-01-16
> **kestrel1 said:**
> Have you got a space in the partition name? If so I think you need to enclose it in speach marks, so it would look like this:
```
sudo mount -t ntfs-3g/dev/hda5/media/"For All" -o force
```

^

---

### Post by zasf on 2008-01-16
> ```
sudo mount -t ntfs-3g/dev/hda5/media/"For All" -o force
```

I don't think you're using the right command, that's why mount prints a lot of stuff, use

```
sudo mount /dev/hda5 /media/For\ All -o force
```

or

```
sudo mount /dev/hda5 /media/For\ All -o force -t ntfs
```

and try avoiding spaces in directory names :)

---

### Post by umarali on 2008-01-17
THANK YOU!!! FINIALLY GOT IT TO WORK!!!
you guys are god sent!!!

---

### Post by ItalOz on 2008-01-25
it happened to me as well like umarali, the point is that if you type "man mount" there is not such an option as "force" to be used with the switch -o
Thus I had the same message as in post #14
Maybe with the line

sudo mount /dev/hda5 /media/For\ All -o force -t ntfs

it works by I did not have the chance to try.

Any explanation?

---

