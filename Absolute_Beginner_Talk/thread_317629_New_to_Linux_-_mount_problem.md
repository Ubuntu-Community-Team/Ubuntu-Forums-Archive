---
title: "New to Linux - mount problem"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by -=J_D=- on 2006-12-12
I have recently installed ubuntu on my old windows-me machine.

I have 2 hdd's, one reformatted during the install of ubuntu, the other containing important documents / photos / videos so i cannot reformat this.

I am having trouble mounting the second hdd, i have been searching through multiple forums and tutorials on the net but i always seem to get stuck somewhere.

I have tried using this code
/dev/hdb1 /media/datadrive vfat  umask=0222,dmask=0000,uid=0002,gid=users,users  0 0
but i keep getting permission denied so i tried to follow the tutorial here [http://www.smorgasbord.net/book/export/html/195](http://www.smorgasbord.net/book/export/html/195)
but i also find myself getting permission denied.

What i am intending to do on this computer is install samba and share this second drive over a windows / linux network. The drive need both read / write capabilities.

If someone can give step by step instructions on how to mount my second hdd id really appreciate it, because atm i have no idea what i am doing.

Thanks

---

### Post by raul_ on 2006-12-12
What format is the drive u want to mount?

---

### Post by bodhi.zazen on 2006-12-12
Mounting and permissions depends on the file system:

_Windows:_

For read-write: [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
[list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and umask=000[/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)

To mount at boot you will need to edit /etc/fstab (as outlined in the links above). For an overview of fstab see:
[How to fstab]()
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

See also [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by raul_ on 2006-12-12
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows")

This one has never failed me :rolleyes:

---

### Post by -=J_D=- on 2006-12-13
Hey thanks, i got it all working great!!!

---

