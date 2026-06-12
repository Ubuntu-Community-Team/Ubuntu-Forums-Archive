---
title: "NFSU on Cedega"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-07-19
i currently have the 2 ISO's for NFSU

how would i go about installing the game on Cedega?

---

### Post by splintercellguy on 2007-07-19
Cedega? Why not plain Wine? Get the latest from [http://winehq.org](http://winehq.org). It would be a simple matter of running the installer under Wine then testing the game. Do file an AppDb report if desired :).

---

### Post by skymera on 2007-07-19
installer?
its an ISO.
how do i mount it?

i tried wine it wouldnt work.
some one else said cedega so i went and go it.

---

### Post by splintercellguy on 2007-07-19
To mount an ISO, first make a mount point:

sudo mkdir /mnt/<wutever>

Then mount:

sudo mount -t iso9660 /path/to/ISO/file/file.iso /mnt/<wutever> -o loop,ro

---

### Post by skymera on 2007-07-19
that dosent work :(
neither does anything else
```

scott@scott-desktop:~$ sudo mount -t iso9660 /home/scott/Desktop/nfsu/disc 1.iso /mnt/disc1 -o loop,ro
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
scott@scott-desktop:~$ 

```

---

### Post by frodon on 2007-07-19
The question is where did you get the iso, as for using cedega you can just check the documentation or open a support ticket to cedega, they will assist you.

---

### Post by skymera on 2007-07-19
my mate copied over his ISO to me

and i'll try that

---

### Post by splintercellguy on 2007-07-19
First off, you need to escape your spaces, like this

...disc\ 1.iso

and you need the options too

-o loop, ro

Oh yeah, make sure to fire up winecfg and add the mount path to your Drives, and set type as CD-ROM.

---

