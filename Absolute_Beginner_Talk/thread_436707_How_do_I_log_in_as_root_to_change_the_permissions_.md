---
title: "How do I log in as root to change the permissions on /media/disk?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by krazejpo on 2007-05-08
How do I log in as a super user in Ubuntu Feisty Fawn so that I can change the permission on a 2nd hard drive that doesent contain windows.

---

### Post by justleen on 2007-05-08
dont logon as root. use sudo instead

sudo -i at a terminal will give you a "root" terminal.

Root is disabled, and thats for a reason :0

---

### Post by Skrynesaver on 2007-05-08
```
sudo chown <newOwner:newGroup> /media/disk
```

---

### Post by krazejpo on 2007-05-08
sudo chown <newOwner:newGroup> /media/disk

doesent work

---

### Post by rich.bradshaw on 2007-05-08
assumedly you put in what owner, group and disk you wanted....

---

### Post by krazejpo on 2007-05-08
right now the owner is root and the group is root, but i would like to change it to kraze. Please Help!

---

### Post by LaurelLynn on 2007-05-08
Owner and group usually default to the same thing, so:

$   sudo  chown kraze   /media/disk
$   sudo  chgrp kraze   /media/disk

---

### Post by krazejpo on 2007-05-08
I fixed the problem thanks to my friend Machinevirus, all I had to do is go to synaptic package manager, search for ntfs-config and install it. After that you look for it in Applications- System Tools- NTFS Configuration Tool and then enable write support for internal device. click ok. And now you can write and delete files on it! TRUST ME IT WORKS!!!! Create a folder in it and see for yourself!!!

---

