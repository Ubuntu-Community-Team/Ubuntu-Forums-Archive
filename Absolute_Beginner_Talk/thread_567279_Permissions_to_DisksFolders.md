---
title: "Permissions to Disks/Folders"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by aas452 on 2007-10-04
I am haveing trouble giving permission to a user or even to root through the GUI. I change the opions and then the changes never save.

I am thinking I need to do this throught the terminal. An instructions or direction to somewhere I can find  how to accomplish this.

---

### Post by nest on 2007-10-04
are you doing the changes of the permissions being root? (sudo nautilus)

and, you cannot change permissions to the root, root is like god, he can do whatever he wants.

---

### Post by asmoore82 on 2007-10-04
> **aas452 said:**
> I am haveing trouble giving permission to a user or even to root through the GUI. I change the opions and then the changes never save.

I am thinking I need to do this throught the terminal. An instructions or direction to somewhere I can find  how to accomplish this.

are you trying to save/store permission on a non-*NIX filesystem such as FAT or NTFS?

---

### Post by aas452 on 2007-10-04
yea its actually a NTFS format, 

on another note do you recomend a particluar format to use???

---

### Post by bodhi.zazen on 2007-10-04
NTFS does not support permissions. You set them at the time of mount or with ntfs-config.

sudo mount /dev/xxx /mount/point ntfs-3g -o uid=1000,gid=100,umask=007

Or put those options in fstab

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by aas452 on 2007-10-04
Thanks all going 2 give it a try 2Morrow. The more I spend on Linix the more I wonder why others arn't swithing, thanks agian

---

