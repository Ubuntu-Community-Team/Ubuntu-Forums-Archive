---
title: "Error trying to acess WinXP NTSF Partition"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by edurm on 2005-10-05
I'm trying to mount my WinXP NTSF partition hda1 
```
root@ubuntu:~# /dev/hda1 /mnt/windows ntfs auto,umask=0,ro 0 0
bash: /dev/hda1: Permission denied
```
am I misstyping something ? :confused: 
I got this info from: 
/dev/hda1 /mnt/windows ntfs auto,umask=0,ro 0 0

---

### Post by SilentCacophony on 2005-10-05
Check this out:

[http://www.ubuntuguide.org/#automountntfs]("http://www.ubuntuguide.org/#automountntfs")

---

### Post by Hobbsee on 2005-10-05
[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

Follow those commands - the /dev/hda1...etc is actually in a document opened with gedit...

---

### Post by edurm on 2005-10-05
Thank You very much, I'll be checking it out tomorrow

---

### Post by edurm on 2005-10-08
[QUOTE=edurm]Thank You very much, I'll be checking it out tomorrow[/QUOTE]



It works, thks!



Now to access the WIN-XP NTSF partition I just need to go to /media/windows ;) 



But Can I create a shortcut to desktop or to my computer of this partition ? 


is it possible :(

---

### Post by edurm on 2005-10-08
I found the answer:


2) Everynow and then I like to use Gnome, only thing is how on earth do I create a shortcut to another directory? So that it will show up on my desktop?

The easy way is to open nautilus (the file manager) find the folder you wish to make a link to on your desktop, and drag it with the middle button to your desktop. You'll be asked what you want to do. Move here, copy here or link here. Select link. That way the folder will still be in the same place and you'll have the equivalent of a Windows shortcut to it on the desktop.

---

