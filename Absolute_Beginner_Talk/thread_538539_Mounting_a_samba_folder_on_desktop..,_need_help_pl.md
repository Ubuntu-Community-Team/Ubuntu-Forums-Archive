---
title: "Mounting a samba folder on desktop.., need help plz"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-08-30
Hello.
I'm trying to mount a windows network sared folder on my desktop in order to direct access to these files and play them with VLC.

I found some old topics in this form witch explain how to do it, 

first install: 
>  sudo apt-get install smbfs

Then the mounting:
> sudo mount -l smbfs -o username=administrador, password=MIXIM, ip=192.168.0.248, workgroup="" //192.168.0.248/TS0/MULTIMEDIA/MEDIATECA/VIDEO /home/Desktop/Video


But when mounting I'm not getting any answer. Just this:

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
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


Do I'm mistaking somewhere?

Plz help!!

---

### Post by schorsch on 2007-08-30
..... use "mount -t ....." ("t" means "type"). You used a lowercase "L" instead of a lowercase "T" ...

---

### Post by Kosimo on 2007-08-30
> **schorsch said:**
> ..... use "mount -t ....." ("t" means "type"). You used a lowercase "L" instead of a lowercase "T" ...

Tried with mount -t but got exactly the same answer:

 > sudo mount -t smbfs -o username=administrador, password=MIXIM, ip=192.168.0.248, workgroup="" //192.168.0.248/TS0/MULTIMEDIA/MEDIATECA/VIDEO /home/Desktop/Video
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


---

### Post by schorsch on 2007-08-30
... you could try "cifs" instead of "smbfs" .....

---

### Post by justleen on 2007-08-30
what i usually do is type in the nautlius bar
smb://server.name.local/share
then drag it to the sidebar (or desktop..).  not sure if thats what your looking for, but it works for me

---

### Post by Kosimo on 2007-08-30
> **schorsch said:**
> ... you could try "cifs" instead of "smbfs" .....

Still not working... :(  >  sudo mount -t cifs-L username=administrador, password=MIXIM, ip=192.168.0.248, workgroup="" //192.168.0.248/TS0/MULTIMEDIA/MEDIATECA/VIDEO /home/Desktop/Video
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


I can't understand where I'm mistaking,... Should be right...

---

### Post by Kosimo on 2007-08-30
> **justleen said:**
> what i usually do is type in the nautlius bar
smb://server.name.local/share
then drag it to the sidebar (or desktop..).  not sure if thats what your looking for, but it works for me

Hi.
This is not exactly what I'm looking for. Cuz by doing this I'm just creating a shutcut, and what I need to do is to mount this folder on my local computer in order to use VLC that doesn't works with SAMBA folders.

---

### Post by Kosimo on 2007-08-30
Any other answer? I really need to have this folder mounted now (I'm working) but definitely can't do it by myself....

Heeeeelp!!!!

---

### Post by Kosimo on 2007-08-30
:cry: :cry: :cry: :cry:

.....

---

### Post by aitorcalero on 2007-08-30
Why don't you try with pyNeighborhood? You can install it through Synaptic, it's a GUI for Samba, very easy to use.

---

### Post by Kosimo on 2007-08-30
> **aitorcalero said:**
> Why don't you try with pyNeighborhood? You can install it through Synaptic, it's a GUI for Samba, very easy to use.

Hey, thank you for the answer!

I just installed pyNeighborhood, and it looks quite easy. But now I'm having problems here. Has been difficult for me to understand where to save passwords in order to access to the remote computer. Now is done and I can see my computer anb the shared resources.
But, when trying to mount them by double click it just appears a small window saying.
Failed to mount...

And stopped here again... !!!  


:(

---

### Post by schorsch on 2007-08-30
Back to the original command: "Damned Spaces!" ;-)
It was hard to recognize but you have spaces after the commas which separate the options after the parameter "-o". So the mount command thinks the option "password" is parameter for the mount command and not another option. Remove the spaces and you should be done .....

---

### Post by Kosimo on 2007-08-30
> **schorsch said:**
> Back to the original command: "Damned Spaces!" ;-)
It was hard to recognize but you have spaces after the commas which separate the options after the parameter "-o". So the mount command thinks the option "password" is parameter for the mount command and not another option. Remove the spaces and you should be done .....

Wow!! I didn't realize it!! I should be more careful when typing code into terminal 


But anyway I'm not using the command anymore, I'm using  pyNeighborhood and finally I got it working 

Danke so much! :)

---

