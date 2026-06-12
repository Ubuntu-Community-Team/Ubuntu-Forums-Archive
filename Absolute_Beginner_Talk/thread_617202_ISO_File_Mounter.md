---
title: "ISO File Mounter"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-11-19
I am trying to make a custon made script to mount ISO files, it uses a enviornment variable called $ISO_PATH
is being set correctly, but the problem comes when i try this:

# mount \$ISO_PATH /media/ISODrives/ -t iso9660 -o loop
$iso_path: No such file or directory

while with escaping the environment variable, i get:

```

mount $ISO_PATH /media/ISODrives/ -t iso9660 -o loop
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

```


PS:
I know its not actually related to Ubuntu, or a beginner's stuff, but can you help me?

---

### Post by hyper_ch on 2007-11-19
it shouldn't be
```

\$ISO_PATH

```

but

```

/$ISO_PATH

```

---

### Post by shoaibi on 2007-11-19
Errors:
```

chevaliar@eagles-nest:~/Documents$ export iso_path='/media/sda5/Academics/Co-Curricular/Video Lectures/Linux tutorial/Shell Fundamentals.iso';
chevaliar@eagles-nest:~/Documents$ sudo mount /$iso_path /media/ISODrives/ -t iso9660 -o loop
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

```


PS:
can i mount rar/mdl etc files this way as well, or do i need some other script or command?

---

### Post by hyper_ch on 2007-11-19
I guess you have to escape your path:

e.g. change this:
```

Video Lectures

```

to this:
```

Video\ Lectures

```

---

### Post by shoaibi on 2007-11-19
```

chevaliar@eagles-nest:~$ export iso_path='/media/sda5/Academics/Co-Curricular/Video\ Lectures/Linux\ tutorial/Shell\ Fundamentals.iso';
chevaliar@eagles-nest:~$ echo $iso_path
/media/sda5/Academics/Co-Curricular/Video\ Lectures/Linux\ tutorial/Shell\ Fundamentals.iso
chevaliar@eagles-nest:~$ sudo mount /$iso_path /media/ISODrives/ -t iso9660 -o loop
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

```

---

### Post by roaldz on 2007-11-19
iso files contain a filesystem, like iso9660. Rar files do not use a filesystem, they just use a compression method like zip. please remember: you mount a filesystem, not a device. A Filesystem!

Well, this is what i get:

```
roald@roald-laptop:~$ export iso_path=/media/sda5/iso/pfSense.iso
roald@roald-laptop:~$ export
...blahblahblah.....
declare -x iso_path="/media/sda5/iso/pfSense.iso"
roald@roald-laptop:~$ sudo mount $iso_path /mnt/temp/ -t iso9660 -o loop
[sudo] password for roald:
roald@roald-laptop:~$ ls /mnt/temp/
bin           cf            COPYRIGHT  etc      libexec  pkg_info.txt  rescue  scripts                 usr
boot          conf          dev        kernels  media    proc          root    tmp                     uzip
boot.catalog  conf.default  dist       lib      mnt      RELENG_1_2    sbin    trigger_initial_wizard  var
roald@roald-laptop:~$ 


```

note:
did not use export with single or double quotes, and did not prepend a slash or a backslash before $iso_path in the mount command.
Hope this helps!

Roald

---

### Post by shoaibi on 2007-11-19
@roaldz:
what's this:
roald@roald-laptop:~$ export
...blahblahblah.....
declare -x iso_path="/media/sda5/iso/pfSense.iso"

and also still i am getting the same long explaination on how to use moutn command correctly, even if i remove quotes...

---

### Post by dark_harmonics on 2007-11-19
i created a directory under my /media folder (so it mounts to the desktop) so i run this command to mount iso files:

sudo mount -o loop /pathtoiso.iso /media/iso

It seems that i dont need to specify the filesystem type.

I use this command to create iso files from the CD/DVD drive

dd if=/dev/scd0 of=blah.iso


the if= part will be whatever your cd/dvd block device name is. You can find that out by typing ls -l /dev/cdrom.

Hope any of this helps.

---

### Post by sparkiegeek on 2007-11-19
The problem is the spaces in your variable. The shell is expanding the path into separate words (which you don't want). The reason you're getting the mount help printed out is because mount is being given more than two arguments.

Try this:
```
mount "$ISO_PATH" /media/ISODrives/ -t iso9660 -o loop
```

Double quotes around the variable ensure that mount only sees the two arguments that you want

PS: Refer to the Advanced Bash Scripting Guide for all the gory details: [http://tldp.org/LDP/abs/html/quotingvar.html](http://tldp.org/LDP/abs/html/quotingvar.html)

---

