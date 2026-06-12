---
title: "File Browser slooooooow on smbfs mounts"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by thewump on 2007-01-26
So..

I have one XP box that mount to for various reasons.

If I connect to it using CTRL-F2 and entering the IP,  I can browse it like lightning

When I create mounts to it using fstab entries like:

//192.168.1.69/share /localdir smbfs credentials=/home/keith/.config/.smbpassword,gid=1000 0 0

it is sooooooooooo slow,  even when I browse into a folder that CONTAINS the folder which is mounted.  

e.g.

I have $HOME/pictures
containing:
$HOME/pictures/random ( a local folder )
$HOME/pictures/picturebank ( a mount on the xp box )

Even going into $HOME/pictures itself takes about 30 seconds to respond.

The only difference I see is that file browser tries to make icons on the mounted directory.. Is this is?  Is there some kind of read ahead?

TIA

Keith

---

### Post by thewump on 2007-01-26
yo mama bump

---

