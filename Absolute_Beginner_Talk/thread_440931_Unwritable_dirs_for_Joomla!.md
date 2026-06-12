---
title: "Unwritable dirs for Joomla!"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Arkanos on 2007-05-12
Hi all, I'm installing Ubuntu on all my PCs, I'm really happy about this OS.
I'm here to ask you a little question.
I'm "porting" my projects from Windows to Ubuntu 7.04.
I've installed XAMPP (following this tutorial [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)) ad everything works good, but after Joomla installation, I have seen some problems.
I can't upload my modules or my components because the directories are Unwritable.
I've searched trought the forum, but I haven't found any suitable solution.

Someone could help me??

---

### Post by mech7 on 2007-05-12
They need to be set writable either by chmod or open as administrator and set them to read / write by others.. Also PHP can be setup to have it's own user rights i belive which is the safest.

---

### Post by mthakur2006 on 2007-05-12
that was probably because you have installed something where you need root privileges to write to it. Try changing the unwritable directory to be in your home folder, then you should be able to do it.
thanks,
mthakur2006

---

### Post by Arkanos on 2007-05-12
I  can do this with command?
```
sudo chmod 777 /myname/public_html/
```

Sorry but I'm a newbie, could you be a little bit more tutorialized! :lolflag:

---

### Post by paparucino on 2007-05-12
> **Arkanos said:**
> 
I can't upload my modules or my components because the directories are Unwritable.
I've searched trought the forum, but I haven't found any suitable solution.

Someone could help me??

```

sudo apt-get install ntfs-3g

```

then mount, in /etc/fstab, your windows disk this way
/dev/sda1     /media/the name you like      ntfs-3g    defaults      1 0

From time now you should be able to write to  NTFS partitions

---

### Post by Arkanos on 2007-05-12
The problem was easier! :) 
I've clicked with the right mouse button on the directory with my local Joomla installation->properties->permissions (granted all).
Now every dirs are Writable! :KS

---

### Post by Arkanos on 2007-06-02
I used exactly:
> sudo chmod -R 777 <DIR>

---

### Post by garyedwardjohnston on 2008-05-30
I've been working on this for3 straight days now and am very frustrated.

Can someone pls provide complete details about this.

Thanks.

Ubuntu Hardy / XAMPP 1.6.6 / Joomla 1.0.15

---

