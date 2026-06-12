---
title: "How to mount/unmount network folders manually, and allow all users to read"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-08-01
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite)

This doesn't seem to work.  I am following these instructions and this is what I am getting...

```
sudo mount //10.10.10.82/Wdrive /media/Wdrive -o username=username,password=password, dmask=777,fmask=777
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
```

I thought maybe that command was missing the "-t" or the "smbfs" part of the line that I am used to using.  So I tried it with the "-t" and I get this...


```
sudo mount -t //10.10.10.82/Wdrive /media/Wdrive -o username=username,password=password, dmask=777,fmask=777
mount: mount point dmask=777,fmask=777 does not exist
```

Ideally I want to set these into my FSTAB file so that it will mount upon boot, but I want to get this working first.

Now, if I do it this way.... it works.... BUT, it sets the owner of the mounted shares to ROOT and I cannot do anything but READ ONLY from the folders.
```

sudo mount -t smbfs -o username=username,password=password  //10.10.10.82/Zdrive /media/Zdrive
```

---

### Post by jimrz on 2007-08-01
take a look [[COLOR="Sienna"]**_here_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=280473") it might fit your need

---

### Post by kc5hwb on 2007-08-01
That almost works.... his suggestion is to use this command.,..

```
sudo smbmount //192.168.1.2/Music /home/dbott/music -o username=dbott,password=mysecretpassword,uid=1000,mask=000
```

But when I try that, it sets the owner of the mount point as my username, but it sets the group owner to ROOT.  So essentially it is the same issue.... still Read Only.

---

### Post by jimrz on 2007-08-01
from the terminal try
```
sudo chmod -R a+rwx /home/dbott/music
```

adjust the path to whatever you call your mount point for the share

---

### Post by kc5hwb on 2007-08-01
well, on the local folder, I have already set it to 

```
sudo chmod -R ugo+rwx /my/local/folder
```

which of course opens it up completely.  But these permissions are over-written once I mount it to the network share.

---

### Post by jimrz on 2007-08-01
> **kc5hwb said:**
> well, on the local folder, I have already set it to 

```
sudo chmod -R ugo+rwx /my/local/folder
```

which of course opens it up completely.  But these permissions are over-written once I mount it to the network share.

you need to set the permissions of the folder on it's host machine and also the permissions for the mount point on the other user's machine on their machine

---

### Post by sochbat on 2007-08-01
So i just got my slave HD to mount, but its always manually.

Is there a command to have it mounted, and ALWAYS be there on the desktop?

---

### Post by kc5hwb on 2007-08-01
I've already done all that.  I should have mentioned at first.... all these machines are on a network at my home.  I have 3 Ubuntu boxes on this network, 2 of them desktops and this laptop (which is the one I have been working with tonight)  The 2 desktops can see each other fine, full RWX access and all that... no problems at all.  But when I try and mount from this laptop, with the same process I did for the 2 desktops, it doesn't seem to want to work.

---

### Post by kc5hwb on 2007-08-01
> **sochbat said:**
> So i just got my slave HD to mount, but its always manually.

Is there a command to have it mounted, and ALWAYS be there on the desktop?

Try this

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by jimrz on 2007-08-01
> **kc5hwb said:**
> I've already done all that.  I should have mentioned at first.... all these machines are on a network at my home.  I have 3 Ubuntu boxes on this network, 2 of them desktops and this laptop (which is the one I have been working with tonight)  The 2 desktops can see each other fine, full RWX access and all that... no problems at all.  But when I try and mount from this laptop, with the same process I did for the 2 desktops, it doesn't seem to want to work.

might try checking /etc/samba/smb.conf on the laptop and comparing to one of the ones that is working.

---

