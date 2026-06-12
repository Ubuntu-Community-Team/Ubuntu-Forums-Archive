---
title: "Mount Windows Share Issues"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by broth420 on 2007-07-07
I am trying to mount a windows share on a Win2003 server using CIFS
I have followed these instructions:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

but every time I reboot, the drives are gone and are not re-mounted.
If I cd to the dirctory and then type dir, there is nothing available.
I then type in sudo mount -a 
and nothing happens.  If I back out and then type in sudo mount -a and then cd back into the directory, the mount works.

any ideas?  my fstab lines for the network drives are:

//192.168.0.11/flac    /home/samba/flac        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.0.11/mp3    /home/samba/mp3        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

as I mentioned before, when I first entered these lines and saved the file, I did a sudo mount -a, and the drives mounted.  It is just on reboot that it doesn't work.
Thansk, Bill

---

### Post by trinaryouroboros on 2007-07-09
I will send you my mount stuff when I get home, but, I've been tackling these baddies since Hoary Hedgehog edition and I know how frustrating it can be sometimes.

By the way, interestingly enough, since Feisty Fawn all I've had to do - to get network shares easily opened by GUI is click Places -> Network -> Your2k3server, then right-click the share and just make a link.

That's the easy way out, however. If you need an actual Mount point because you do a lot of SSH or something, it can be a little work.

Like I said I'll send you some more info when I get home later.

Bad link before, also check this out:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

See if it works without cifs...

---

### Post by broth420 on 2007-07-09
Thanks for the link.  I followed the link's instructions, and it still doesn't automount at boot.  I have to type in sudo mount -a, and then the shares are there.  Any help would be great.
Thanks again.

PS.  this is on server, so no GUI (and if I can help it, I would like to avoid one)

---

### Post by trinaryouroboros on 2007-07-09
Hmm, now that I think of it I'm not even sure I remember how I pulled this off...I set this fstab up on Hoary Hedgehog quite some time ago:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5       none            swap    sw              0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
# /dev/hdf1       /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdf5       none            swap    sw              0       0/dev/hdb             /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd1       /media/olddrive      ntfs    nls=utf8,umask=0222  0 0
//W0-RM-H0-L3-FF/BUSLINK  /media/buslink  smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777   0     0
```

Maybe smbfs fakes its way in? Not sure.

:confused:

---

### Post by broth420 on 2007-08-06
here is a trick I learned from a friend of mine.  Simply write a script to have the mount take place at boot.  The downside of this is having a password in clear text.  There may be a way to fix ths however.  Anyone?

Edit this file:

/etc/rc.local

Add these lines:

sleep 10
sudo mount -t smbfs -o username=username,password=password //192.168.1.31/albums /mnt/music

---

