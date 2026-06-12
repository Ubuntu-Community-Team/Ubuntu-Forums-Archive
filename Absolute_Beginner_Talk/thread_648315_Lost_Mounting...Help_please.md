---
title: "Lost Mounting...Help please"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by stenella on 2007-12-23
Right, I did a dumb thing without realizing it...Noob, right? I nneded to put some data from another computer (Windows) onto my HP pocket drive, it seems I unplugged it too soon, I thought Ubuntu had shut down. When I went to access it again I got a big error message saying 'can't mount volume ' this is apparently due due to an 'unclean shut down' (ick).

I tried using the terminal and putting in the command suggested to force it, no luck. The next suggestion is to do similar by adding a line to the /etc/fstab file.I don't know how to find that, I'm afraid. I've tried a search for answers but had no luck so far.

I don't have Windows working on the computer anymore, so I can't do the other suggestion, which involved windows 'safe removal'

Can anyone help please, I really need to get at the data on that drive - which currently is Ntfs
Cheers

---

### Post by eolson on 2007-12-23
Maybe the system thinks it's still mounted ... go to Places Computer and see if it happens to be listed.  If so umount it.

---

### Post by rustutzman on 2007-12-23
From another thread I was able to get by my drive mount issues by installing PySDM through add/remove. 

That will give you Storage Device Manager in your System - Admin menu. HTH

Russ

---

### Post by blueridgedog on 2007-12-23
You can try and force the mount when you tried mounting it before it gave you a device ID, something like /dev/sdc1, so using that as an example, you could:

sudo mount /dev/sdc1 /media/??? -o force

You would replace sdc1 with the actual device and ??? with the directory/mount point that you have used for this in the past.

---

### Post by stenella on 2007-12-23
Hi,
eolson: No, the compute has it marked as unmounted.
rustuzman: I downloadedand installed PSYDM, but when I open the programme there's nothing but an empty window, no drives.
blueridge dog: I entered the force command with the name of the drive and got this:

fraser@Quinta-desktop:~$ sudo mount -t ntfs-3g/dev/sdg5/media/HP Pocket Media Drive -o force
[sudo] password for fraser:
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

I have no idea what this all means. I get the general drift, but don't want to screw things up...
Cheers

---

### Post by poorbadger on 2007-12-23
Are you sure you were trying to mount the correct device?

I only ask because I had that problem a couple days ago.  I believe the info re: the mount syntax in the error message is an example and you might have to play around w/ it. I ended up saving the data on a disk gone bad under windows w/ the force option.

Good luck!

mount -t [filesystem type] [device] [mountpoint] -o force

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by stenella on 2007-12-23
Poorbadger, now you've got me worried, The name I banged into the terminal is the only one I know for an HP pocket drive, It's the only removable drive I have on the machine at the mo

---

### Post by eolson on 2007-12-23
O.K.  I don't have an HP drive,  but was able to get about the same problem (I think) with a flash drive.  

I unmounted it properly (I'm chicken)
Then went to Places Computer and tried right click  mount volume and get the error message unable to mount media

I unplugged the Flash drive and plugged in back in and it mounted.

---

### Post by blueridgedog on 2007-12-23
> **stenella said:**
> 

fraser@Quinta-desktop:~$ sudo mount -t ntfs-3g/dev/sdg5/media/HP Pocket 

I can't tell from the above, but did you put a space after ntfs-3g and sdg5?  It shoudl be:

sudo mount -t ntfs-3g /dev/sdg5 /media/HP Pocket Media Drive -o force

---

### Post by stenella on 2007-12-23
Hi again.
eolson: When I right click on the pocket drive I don't get the option of unmounting, only 'mount'.

blueridgedog. just thesame. To double check, I pasted yours ibn and got the same reply.

---

### Post by blueridgedog on 2007-12-23
The error you are getting is due to spaces in the name.

Try this command:

sudo mount -t ntfs-3g /dev/sdg5 "/media/HP Pocket Media Drive" -o force

If that fails, send me a copy of what you get with:

ls -al /media

and

cat /proc/partitions
(with the thumb drive in and with it out)

---

### Post by stenella on 2007-12-23
Got it, ls -al /media did the trick..... Dare I ask how, or will the answer give me a migraine?:)
Thanks very much, blueridge dog and the rest of you who took the time to help, much appreciated. It gives a person confidence to stick with Ubuntu when coming from the sheltered environment of Windows!

---

### Post by blueridgedog on 2007-12-23
The problem (and I mocked it up here to get you the right advice) is that you can't have spaces in a mount target name, so

sudo mount -t ntfs-3g /dev/sdg5 "/media/HP Pocket Media Drive" -o force
works
but
sudo mount -t ntfs-3g /dev/sdg5 /media/HP Pocket Media Drive -o force
fails if run by hand

I can only assume since the name "HP Pocket Media Drive" was given by the system, that the auto mounting features escapes the spaces.

I was only able to test it because I have a 4 gig flash drive here that I am using to test Vista's "Ready Boost" with.

---

### Post by stenella on 2007-12-24
Got it. Thanks for the explanation.

---

