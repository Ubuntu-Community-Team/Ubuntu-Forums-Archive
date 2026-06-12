---
title: "Dapper AMD 64 NTFS trouble"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by RedKudos on 2006-10-18
To the experts or the more advanced than me.

After playing with sudo gedit /etc/fstab and man mount, ntfsmount for hours i seem to be getting now where.

if i blank the additional lines refering to my SATA drive (/dev/sdb1) and just allow the system to boot using the pmount.allow file then i get instant access (read only) to the drive.

if i use the line

/dev/sdb1	/media/windowsdata	ntfs	rw,users,owner	0	0

then it mounts ok, but i get permission to view errors
if i use the similar line of ntfs-fuse <<atribs>> then it kicks an error saying the ntfs-fuse not recognised allthough i can get it to mount correctly from the tutorial.

and lastly and most annoyingly i have tried to follow the tutorial to get ntfs-3g working.

and after adding and removing the addresses from the tutorial manually to the sudo gedit /etc/apt/sources.list i keep getting an error when i execute the update command. it goes along of the lines of "problem with repos.. may not be online..... 404 not found" to which i am wondering is this strictly 32bit? and not for 64.

any help would be appreciated.

---

### Post by taurus on 2006-10-18
For your NTFS, why not do something like this in /etc/fstab?

```

/dev/sdb1 /media/windowsdata  ntfs  defaults,umask=0222   0   0

```

---

### Post by Chickencha on 2006-10-18
Well, I've got NTFS read/write support set up on my 64-bit Dapper system.  I followed the guide here to get it to work: [http://wiki.linux-ntfs.org/doku.php?id=ntfsmount](http://wiki.linux-ntfs.org/doku.php?id=ntfsmount)

I first went through the "install ntfsmount (generic)" section, followed by the "using ntfsmount" section.  Everything works perfectly.  Hopefully that helps.

---

