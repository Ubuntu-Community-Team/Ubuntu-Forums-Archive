---
title: "NTFS support in Linux"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by MakLeod on 2007-05-29
I just allowed write access to two of my NTFS drives and I am wondering how the NTFS support is now in Linux?  Can I be fairly safe in writing to my NTFS drives without the possibility of corrupting data or losing information?  It [I]seems[I/] that NTFS support is fairly rock solid now, is that true?  Thanks in advance.

---

### Post by SoulinEther on 2007-05-29
I don't believe it's that "rock solid"... it's not rock solid enough for me to be risking it, hehe.

---

### Post by Inxsible on 2007-05-29
I have been using it since a few months and I havent had any problems with it yet !!!

Now have I heard anyone else having trouble !

Don't know how much that helps you...but there's atleast 1 vote from me :)

On the other hand .... No software is ever 100 % bug free..........just that you havent seen that bug yet  !!!!

---

### Post by MakLeod on 2007-05-29
Yea, I think I'm just going to allow write access to my extra data partition, instead of allowing access to my windows system partition as well.  Any other experiences writing to NTFS partitions in Linux over a long period of time?

---

### Post by shrinkpad on 2007-05-29
You should use ntfs-3g if you want to write to NTFS or you will break it!

it's in all of the repositories;

apt-get install ntfs-3g

/dev/hda1 /media/hda1  ntfs-3g silent,user_xattr,umask=0,locale=en_US.utf8 0 0

I have been using this for over a year now with no problems.

---

### Post by (chubbstar) on 2007-05-29
ive been using ntfs-3g for ... well since it came out and i havent had a single issue or lost byte with it.

---

