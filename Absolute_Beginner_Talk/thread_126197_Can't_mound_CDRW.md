---
title: "Can't mound CDRW"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by Cysman on 2006-02-05
Hi folks,

I tried to mount my CDRW and this is what the silly thing told me.  How do I resolve this???  I got the same message when I burned a song using sudo gnomebaker but it proceeded to burn the disk.  When I tried to access the file on the cd, it gave me this write protected message also.



kenoutten@ubuntubedroom:~$ sudo mount /media/cdrom1/ -o unhide
mount: block device /dev/hdd is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Cysman on 2006-02-05
Can anyone help?  I also used sudo serpentine and it apparently burned the file but I still can't mount my CDRW!!!!!

---

### Post by Ocxic on 2006-02-05
ubuntu should put an icon on your deskop autmatically but try this command.

sudo mount -t iso9660 /dev/hdd /media/cdrom0

i dunno what the -o unhide flag is ut the about works on my system.

---

### Post by Cysman on 2006-02-06
Ok, I tried that and this is what it says.  Is there a fix in there somewhere?


kenoutten@ubuntubedroom:~$ sudo mount -t iso9660 /dev/hdd/media/cdrom0
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

---

### Post by 5-HT on 2006-02-06
Hi, there should be a space between the device and mount point.

So instead of: ```
 sudo mount -t iso9660 /dev/hdd/media/cdrom0 
```

It should be: ```
 sudo mount -t iso9660 /dev/hdd /media/cdrom0 
```

HTH

---

### Post by Cysman on 2006-02-06
Thanks for replying:  this is what I get again.  Uuuug!

kenoutten@ubuntubedroom:~$ sudo mount -t iso9660 /dev/hdd /media/cdrom0
mount: block device /dev/hdd is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by 5-HT on 2006-02-06
Was this the first disc you've burned on on Ubuntu?

Seems like there's the possibility that the burn may have not proceded/finalized properly.

Can you try to see if another computer can read the disk?

If not, you can try to see what the problem is by typing ```
 tail -f /var/log/dmesg 
```

and putting the cd in (you can get out of the real-time log by typing ctrl + c).

This will follow the kernel messeges, and my have entries along the lines of "back superblock", "filesystem error", "I/O" error, or something similar.

It that's the case, then unfortunately there were errors when burning the disc, and I would suggest burning at a lower speed (I use 2X myself just to be sure...but it's old hardware).

HTH

---

### Post by Cysman on 2006-02-06
Funny thing, I tried to put in a regular store bought music cd and I got the same error:

kenoutten@ubuntubedroom:~$ sudo mount /media/cdrom1/ -o unhide
mount: block device /dev/hdd is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

But when I put in a cd with pics and video I made on a Windows machine, it mounted just fine. ?????

---

### Post by 5-HT on 2006-02-06
[QUOTE=Cysman]Funny thing, I tried to put in a regular store bought music cd and I got the same error...
But when I put in a cd with pics and video I made on a Windows machine, it mounted just fine. ?????[/QUOTE]

Ok, I believe I know what's going on here.

Audio CDs (as in CDs burned as an audio CD, not just a CD with music on it) are handled a little different than data CDs in that they are not (as far as I know) mounted in the normal sense.

So if you're are trying to mount an audio cd, I believe it's an exercise in futility.

To play an audio cd, one needs just to open up a favourite media player and go from there.

From what you've mentioned it looks like you can mount a data cd you have, but not the audio cd, is that correct?

Or is a data CD you've made on linux not mounting (from your post I'm assuming it's an audio CD...but just to make sure)?

Hope this helps.

---

