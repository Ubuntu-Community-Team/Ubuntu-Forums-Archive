---
title: "unable to edit grub menu"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Gentex on 2007-01-28
Hi, almost certainly a dumb question here . . .

I want to edit my grub load menu to make WinXP the default.  But, I can't edit it as a user and have had no luck logging in as root.  This has been very simple in other distros I've tried, but I've totally hit a wall here.  Help?

Gentex

---

### Post by mikewhatever on 2007-01-28
cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst

:D :D

---

### Post by Stemp on 2007-01-28
[Sudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Aggienator on 2007-01-28
> **Gentex said:**
> Hi, almost certainly a dumb question here . . .

I want to edit my grub load menu to make WinXP the default.  But, I can't edit it as a user and have had no luck logging in as root.  This has been very simple in other distros I've tried, but I've totally hit a wall here.  Help?

Gentex

Check out [GrubEd]("http://www.ubuntuforums.org/showthread.php?t=228104&highlight=GrubEd"). If this link doesn't work search the forums you will find it (wish I had found it ages ago!

Cheers Aggie

---

### Post by ardchoille42 on 2007-01-28
gksudo gedit /boot/grub/menu.lst

sudo should never be used with GUI apps, only CLI apps: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Gentex on 2007-01-29
> **mikewhatever said:**
> cp /boot/grub/menu.list /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst

:D :D

Mike, thanks.  That first command didn't work; got some message that the file didn't exist.  Everything looked right (right directory and right file name) but it just didn't work.  <shrug>

 Decided to use the second command anyway and was able to edit the file as needed.

Much appreciated.

Gentex

---

### Post by Gentex on 2007-01-29
> **Aggienator said:**
> Check out [GrubEd]("http://www.ubuntuforums.org/showthread.php?t=228104&highlight=GrubEd"). If this link doesn't work search the forums you will find it (wish I had found it ages ago!

Cheers Aggie

Thanks Aggie.  I may look into that if I decide I want to do more messing with grub.  Right now, it does what I need it to do. :) 

Gentex

---

### Post by mikewhatever on 2007-01-29
The first command backups the menu file, and obviously, it should have been like this ```
cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
``` lst and not list
You're welcome anyway.

---

