---
title: "changing ownership + mounting harddrives"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by katxor on 2007-03-09
Hi guys!

my fstab looks like this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


i also have hdd and hdb that are running on ntfs filesystem.
how do i write to mount up hdd and hdb  at startup and beeing owned by the user "katxor" not root.

might mention that they are already mounted in kubuntu but they dont show in fstab. and they are beeing owned by root so i cant access my musik and stuff as i want :(

please respond in a baby talk way since im neither very good at english nor linux

kind regards!

---

### Post by dstew on 2007-03-09
How about adding to fstab:

/dev/hdb /home/musik ntfs -o rw,auto,async,uid="katxor",gid="katxor" 0 0
/dev/hdd /home/stuff ntfs -o rw,auto,async,uid="katxor",gid="katxor" 0 0
 
?

---

### Post by katxor on 2007-03-10
hmm, now they wont mount at startup ? :confused: 

want me to copy n paste fstab again?

---

### Post by Crooksey on 2007-03-10
Why not just add ...

```

/dev/hdb1 /home/<username>/Windows1     ntfs     defaults        0       2
/dev/hdd1 /home/<username>/Windows2     ntfs     defaults        0       2

```

You need to have the number 1 at the end of the partition...

Now you don't need to reboot to see if it works, just run...

```

$ sudo updatedb
$ mkdir /home/username/Windows1
$ mkdir /home/username/Windows2
$ sudo mount /dev/hdb1
$ sudo mount /dev/hdd1
$ sudo chmod 777 /home/username/Windows1/
$ sudo chmod 777 /home/username/Windows2/

```

Now navigate to your home folder and see if the files have been mounted, if they have success, if not ill be back from work in 5 hours to help you out some more :)

---

### Post by katxor on 2007-03-10
now they have a little lock on them and telling me i cant access the folders
:(


*edit* i can access the harddrives when im runnung krusader in root mode. not the regular krusader mode. so i guess the harddrive still belongs to root. right? ;)

lol, 2nd *edit*

just formatted "windows2" to fat32. what do i write to mount that up? just switch ntfs to fat32?

---

### Post by Crooksey on 2007-03-10
I think just "vfat"

Did you chmod 777 the folder like i said?

---

### Post by taurus on 2007-03-10
Chmod won't work with vfat or ntfs.  

If you want to mount vfat, then do

```
/dev/hdd1   /media/hdd1   vfat   iocharset=utf8,umask=000   0   0
```
Then, create a new mount point for it.

```
sudo mkdir /media/hdd1
```

---

### Post by katxor on 2007-03-18
there there... have had some crashes so been forced to reinstall a couple of times and been trying to get other things fixed :P
thought i should get started with this again.

i followed your leads and this is what happens when i do sudo mount -a

```
$ sudo mount -a
[mntent]: varning: ingen avslutande nyrad på slutet av /etc/fstab 
mount: monteringspunkten  finns inte
mount: okänd filsystemstyp "dmask=0000"

```

the first row says "warning no finished line at the end of /etc/fstab
2nd row reads " mount point does not exist
3d row "unknown filesystemtype "dmask=0000"

and again this is what my fstab looks like.

```

      # Manuellt monterat

/dev/hdb1 /home/kelio/hdb1 ro,auto,user,fmask=0111,dmask=0000
/dev/hdd1   /home/kelio/hdd1   vfat   iocharset=utf8,umask=000   0   0
```

the strange thing with this is that hdb1 is mounted in /media/hdb1 and owner is root  while hdd1 is mounted in /home/kelio/hdd1 also owner is root...

please help ;)

---

### Post by katxor on 2007-03-25
bump

---

