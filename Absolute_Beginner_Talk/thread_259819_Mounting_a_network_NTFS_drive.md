---
title: "Mounting a network NTFS drive"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by xoppaw on 2006-09-17
So my next n00b question of the day is how to mount a NTFS network drive...or even more specific, is it possible? i've read some threads here outlining how to mount NTFS drives with read/write support, but that's not important. i just need to read the data.  
i already set up the opposite, and now i can mount a samba drive from my linux box in windows, but i need the other way...help is much appreciated

---

### Post by skierkegaard on 2006-09-17
Does the (Places => Connect to server) serve your needs?

---

### Post by xoppaw on 2006-09-17
> **skierkegaard said:**
> Does the (Places => Connect to server) serve your needs?

nope...i'm a fully command prompt user...no GUI's allowed

---

### Post by skierkegaard on 2006-09-17
Ok, how about this command?
mount -t smbfs //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword

---

### Post by xoppaw on 2006-09-17
Password:
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



i get this...am i missing part of the command?

maddox@xoppaw:~$ sudo mount -t smbfs //xoppaw/music /home -o username=maddox, password=####### ord

---

### Post by skierkegaard on 2006-09-17
Apparantly the forum decided to space password into passw ord.

Take that ord out of the end of your command.

---

### Post by xoppaw on 2006-09-17
it still gives me the same thing after taking the 'ord' out

---

### Post by skierkegaard on 2006-09-17
sudo mount -t smbfs //xoppaw/music /home -o username=maddox,password=#######

Removed the space between the ',' and 'p'.

---

### Post by xoppaw on 2006-09-17
well i feel like i'm getting somewhere now...


mount: wrong fs type, bad option, bad superblock on //xoppaw/music,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

any clue what that means?

---

### Post by skierkegaard on 2006-09-17
I was thinking that an smbfs share was what you were going for.  I'm not sure what to try from here.  When someone smarter looks at this, they will probably want to see your /etc/fstab

Try modprobe smbfs as well.

---

### Post by xoppaw on 2006-09-17
thanks for getting me this far at least..i wouldn't have even gotten to here.


is this what i need from /etc/fstab?


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by skierkegaard on 2006-09-18
Did you try modprobe smbfs?

---

### Post by xoppaw on 2006-09-18
> **skierkegaard said:**
> Did you try modprobe smbfs?

can you explain that a litte more? i'm pretty new to this whole thing

---

### Post by skierkegaard on 2006-09-18
modprobe smbfs

Would be to try and reload the smbfs module.  That was my last idea.

---

### Post by xoppaw on 2006-09-18
didn't do anything when i tried that.

---

### Post by Kilz on 2006-09-18
smbfs is a seperate package from samba. You might have to install it.
Aftter that, make a folder to mount the share to. open a terminal type in
```
gksudo gedit /etc/fstab
```
add this line after modifing it
```
//SharingComputerIdOrIpAddress/sharename    /path/to/folder/you/made/to/mount/to      smbfs    username=Guest,password=,fmask=777 0 0
```

---

### Post by xoppaw on 2006-09-18
closer...now it's looking more like a layer 8 (user) issue...it's telling me i have an invalid share now. i've tried using just he ip address changing the capitalization and it still gives me that error....any suggestions

---

### Post by Kilz on 2006-09-18
> **xoppaw said:**
> closer...now it's looking more like a layer 8 (user) issue...it's telling me i have an invalid share now. i've tried using just he ip address changing the capitalization and it still gives me that error....any suggestions

Open up nautilus, click Go, then network, click Windows Network icon, get the computers name there and type it in fstab exactly, click on it, get the shares name and copy it into fstab exactly

---

### Post by xoppaw on 2006-09-18
there is no gui on my linux box at all...

---

### Post by Kilz on 2006-09-18
> **xoppaw said:**
> there is no gui on my linux box at all...

Well the ipadress of the windows machine, and the shares name should work in fstab. It has to be exact name tho, it is case sensitive.
```

//ipaddress/sharename /path/to/folder/onlinuxbox   smbfs    username=Guest,password=,fmask=777 0 0
```

once its in place, reboot, and the share on Windows will be automounted to the folder on linux.

---

### Post by xoppaw on 2006-09-18
sweet that worked really really well...i appreciate the help with this.  i think that i'm going to call it a night now that i got that figured out.

---

