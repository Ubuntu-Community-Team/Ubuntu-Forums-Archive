---
title: "weird error message, help plz!"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by xxFelixDCatxx on 2006-08-13
okay I'm trying to mount a network directory locally, so I can synchronize music and all that good stuff.

I found this [http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read)

and followed all instructions to the letter.  Predictably and according to my luck... it failed.  Everytime I've tried it I get this to work I get the same  error message.

cli_negprot: SMB signing is mandatory and we have disabled it.
5175: protocol negotiation failed
SMB connection failed

anyone got any clues? I'd love to hear them.

---

### Post by xxFelixDCatxx on 2006-08-13
okay, i found an old post

[http://www.ubuntuforums.org/archive/index.php/t-8479.html](http://www.ubuntuforums.org/archive/index.php/t-8479.html)

this sounds right, but i tried disabling encryption and leaving it on both and neither worked!

anyone know of any updated info?

---

### Post by xxFelixDCatxx on 2006-08-13
okay I'm absolutely miffed.  

Synopsis:  I'm trying to mount a server 2k3 directory to a local file in ubuntu 6.06(?) 

using this command
sudo mount //192.168.2.2/D$ /media/sharename/ -o username=Felix,password=*******

I got this error message.
cli_negprot: SMB signing is mandatory and we have disabled it.
5175: protocol negotiation failed
SMB connection failed


after doing some reading [http://www.ubuntuforums.org/archive/index.php/t-8479.html](http://www.ubuntuforums.org/archive/index.php/t-8479.html).  I determined the error message has to be some issue with the handshake process between server 2k3 and samba. And the fix was *supposed* to be entering a -t cifs entry in mount.

so my most recent code looked like this

sudo mount -t cifs //192.168.2.2/D$ /media/sharename -o username=Felix,password=*******

and the output....
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


what in the world am i doing wrong here?!?!

---

### Post by Blindulo on 2006-12-05
Hi Felix.

Inbetween your refering to the mentioned old post and the guide of [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently) I solved the same problem as you had.

However it looks to me (and I'm fairly green admittet) that your mount (or kernen) don't support cifs.

Ones it works it can be put in fstab as the guide suggests, with the cifs as filesystem instead of smbfs, and what the guide misses (according to me) is this syntax of the .smbpasswd:
```

username=DOMAINNAME/validusername
password=validusernamespassword

```
Where "DOMAINNAME/" can be removed from above if not needet

The post is old but now it's here, hopefully this have been of help (at least maybe to myself someday in the future).

Take care - Simon

---

