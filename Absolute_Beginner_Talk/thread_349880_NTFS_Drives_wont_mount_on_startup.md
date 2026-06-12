---
title: "NTFS Drives wont mount on startup"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Copperteeth on 2007-01-30
Hey, I've been using ntfs-3g for some time now, and had no problems until about 10 min ago. I have no idea where to start so I'm just going to say everything I've done recently that could have led to this problem. Today I got an update for fuse, fuse-utils and libfuse2 and had some problems with the update. i got this error:

```
E: /var/cache/apt/archives/fuse-utils_2.6.1-0givre4_i386.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/libfuse2_2.6.1-0givre4_i386.deb: conflicting packages - not installing libfuse2
```

i solved the problem by using

> sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade

and it seemed to get everything working.

later today i read something on digg.com about cleaning up files on ubuntu that aren't needed/waisted space, the guide can be found [HERE]("http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html")

I highly doubt that this guide could have caused any problems as the things i removed were just residual config packages but who knows...

i restarted my computer and the first thing i noticed was my desktop background was gone, its saved on my ntfs drive because i like to keep personal files on a separate hard dive in case problems arise, and this drive is my 250gig ntfs drive... a little off topic but any way...

i checked gnome partition editor and i found that the drives were not even mounted to where they usually are. So i mounted them, nothing happened. i went to access the folder they are mounted to and i got the error:

> You do not have the permissions necessary to view the contents of "hdb1/hda1".

i restarted again to see if anything had maby hiccuped unusually and i got the same problem. i checked synaptic package manager and typed in "ntfs" as a search and i discovered that the item named ntfs-3g is not even installed. TBH i don't even know if it should be or not, so i just left it. I really don't know what i did wrong or where i errored but any help would be appreciated. Thank you in advance.

---

### Post by Copperteeth on 2007-01-30
ok i figured something important out, i can acces the drives under the root nautilus when i mount it with gnome partition manager but it wont mount on startup and i cant access it without being root... i have a feeling that gnome partition editor uses a different driver though, i hope this info helps!

---

### Post by taurus on 2007-01-30
Why don't you mount it in /etc/fstab with the right permissions.

Here's a guide for you.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Copperteeth on 2007-01-30
well its not that i need to mount it, the problem is something changed and it shouldnt have. I just tried to mount my partitons manually by using sudo mount -a and it gave me this error:

```
FATAL: Could not open '/lib/modules/2.6.17-10-generic/kernel/fs/fuse/fuse.ko': No such file or directory
fusermount: fuse device not found, try 'modprobe fuse' first
FUSE mount point creation error: No such file or directory
Unmounting /dev/hda1 ()
FATAL: Could not open '/lib/modules/2.6.17-10-generic/kernel/fs/fuse/fuse.ko': No such file or directory
fusermount: fuse device not found, try 'modprobe fuse' first
FUSE mount point creation error: No such file or directory
Unmounting /dev/hdb1 (BIG ONE)
tyler@tyler-desktop:~$ modprobe fuse
FATAL: Could not open '/lib/modules/2.6.17-10-generic/kernel/fs/fuse/fuse.ko': No such file or directory


```

my fstab is fine, i have it set up so everything should work properly but theirs something funkey going on with fuse. According to the guide i followed months ago i use this line
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hdb1 /media/hdb1 ntfs-3g defaults,locale=en_US.utf8 0 0
it worked until today!

---

### Post by taurus on 2007-01-30
It is looking for module fuse so did you run that command to see what happens?

```
sudo modprobe fuse
```
And if you don't mind, you can post the outputs of these two commands here.

```
sudo fdisk -l
cat /etc/fstab
```

p.s.  I just looked and I have /lib/modules/2.6.17-10-generic/kernel/fs/fuse/fuse.ko.  Did you reinstall fuse-utils (libfuse) again?  Otherwise, try to fall back to ntfs instead of using ntfs-3g for now.

---

### Post by Copperteeth on 2007-01-30
not a problem at all...

> tyler@tyler-desktop:~$ modprobe fuse
FATAL: Could not open '/lib/modules/2.6.17-10-generic/kernel/fs/fuse/fuse.ko': No such file or directory

tyler@tyler-desktop:~$ sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3933    31591791    7  HPFS/NTFS
/dev/hda2            3934        9715    46443915   83  Linux
/dev/hda3            9716        9964     2000092+   5  Extended
/dev/hda5            9716        9964     2000061   82  Linux swap / Solaris

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       30515   245111706    7  HPFS/NTFS
tyler@tyler-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=3339ec78-4699-4b1b-9c11-7388d7e8b904 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=aa2ca544-90e9-4dd1-bb67-44b55b4f8f42 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hdb1 /media/hdb1 ntfs-3g defaults,locale=en_US.utf8 0 0


i really appreciate the help, generally i think you have solved most of my problems taurus, thanks
btw yes i did JUST reinstall, thought it might help as that generally worked for most problems in windows, maby not linux.. and i need ntfs3g because it has better write support, i couldnt get ntfs to work with writing

---

### Post by taurus on 2007-01-30
You cannot write to ntfs with ntfs module at all.  Don't even force it or you will trash your ntfs partition.  If you can backup stuff on that ntfs partition, I recommend you format it to ext3 and then install [http://www.fs-driver.org](http://www.fs-driver.org) so you can read and write to that ext3 partition.  It's a much better solution than trying to write to ntfs from Ubuntu.

---

### Post by Copperteeth on 2007-01-30
i understand the pros and cons of using a ntfs partition in linux but the problem is i cannot just back it up, too much information. i need it for my dual boot. I had ntfs3g working flawlessly and if im unable to get it working again i guess ill just reformat ubuntu, it only takes me like an hour to restore everything to the way it was ne way. Thanks for the help but the problem remains unsolved

---

### Post by givré on 2007-01-31
Have a look at /usr/share/doc/ntfs-3g/README.Debian and follow the install fuse module procedure, that might help.

---

