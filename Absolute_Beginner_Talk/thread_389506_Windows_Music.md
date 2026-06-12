---
title: "Windows Music"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by oscillations on 2007-03-20
Relatively new to Ubuntu, but don't get me wrong, I've had some experience with it and am fairly compatible with the OS...just one question, I have several music files saved on my Windows partition, is there a way I can listen to them on Banshee on Ubuntu?

---

### Post by steve101101 on 2007-03-20
try this to mount the drive in ubuntu to then you can just navigate it in nautalis. 

[http://www.ubuntuforums.org/showthread.php?t=255872&highlight=mounting+smbfs+shares](http://www.ubuntuforums.org/showthread.php?t=255872&highlight=mounting+smbfs+shares)

---

### Post by slimdog360 on 2007-03-20
you can actullay mount the drive as read only at the installer. Of course you would have to re-install so maybe its something to keep in mind next time you install Ubuntu.

---

### Post by steve101101 on 2007-03-20
my link will mount it automatically every time without any excessive reinstall

---

### Post by oscillations on 2007-03-20
OK i've gotten a bit perplexed...thanks for the link, steve bunch o' numbers, but I don't think I have samba and I have no clue what a smbfs is...and doesn't read only mean that you can't write to it?  because i still want to save things on ubuntu!  maybe i'm more of a newbie than i thought :confused:

---

### Post by steve101101 on 2007-03-20
if you need to set up samba use this link

[http://ubuntuforums.org/showthread.php?t=202605&highlight=setup+up+samba+peer-to-peer](http://ubuntuforums.org/showthread.php?t=202605&highlight=setup+up+samba+peer-to-peer)

type this to get the needed packages and install them for file sharing

```

sudo apt-get install smbfs smbclient

```

then 

```

sudo gedit /etc/fstab

```

add this line to the end of the opened file

```
//Server/Data /home/steve/Data smbfs auto,workgroup="MARCUSHOUSE",username="",password="",uid=1000,mask=000
```

the first part is the source and the second is the destination folder. fill in your workgoup, username, ect.

send me a message if you need anymore help.

---

### Post by steve101101 on 2007-03-20
also after you edit the fstab you need to type this line just this one time or you can reboot.

```

sudo mount -a

```

---

### Post by RRS on 2007-03-20
> .....several music files saved on my Windows partition......
On same drive/compuTer as UbunTu?
If so, you don'T need Samba, jusT follow [This guide]("http://www.psychocats.net/ubuntu/mountwindows").

 A loT of oTher good guides/advice on Aysui's siTe also.

Oh, BTW, seem To have losT The lower case T on my keyboard, figgur'd cap was easier o read hen misspells, if no le me know :)

---

### Post by orb9220 on 2007-03-20
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
[https://help.ubuntu.com/community/DrivesAndPartitions](https://help.ubuntu.com/community/DrivesAndPartitions)

Come on guys he does not need samba just to access his files, Samba is overkill just to mount and access a ntfs or fat32 partiton for music files.

I have a fat32 partition that has all my pics,music,movies which xp and ubuntu have access to.
or use ntfg for ntfs partitions.

---

### Post by oscillations on 2007-03-21
Say, thanks for the help.  well , i installed ntfs-3g on my computer through the synaptic package manner, but now when i try to run it on the terminal through ntfs-3g i get this response:

> No device specified.

ntfs-3g v20070920-BETA - Third Generation NTFS Driver

Copyright (C) 2005-2006 Yura Pakhuchiy
Copyright (C) 2006 Szabolcs Szakacsits

Usage:    ntfs-3g device mount_point [-o options]

Options:  force, ro, umask, uid, gid, fmask, dmask, locale, show_sys_files,
          no_def_opts, streams_interface. Please see the details in the manual.

Developers' email address: [email]linux-ntfs-dev@lists.sf.net[/email]
Linux NTFS homepage: [http://www.linux-ntfs.org](http://www.linux-ntfs.org)

gah, what now?

---

### Post by oscillations on 2007-03-21
bump.

---

