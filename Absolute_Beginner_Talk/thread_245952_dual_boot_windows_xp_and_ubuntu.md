---
title: "dual boot windows xp and ubuntu"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by brainchild187 on 2006-08-28
Ok, here's my problem....  I started with a new harddrive, I first installed ubuntu, and then on the next day I installed windows xp.  Well, after I installed windows xp that's all that would start up for me.  So I used the "Super Grub Disk" to try to get my computer to dual boot both systems, but now all I can get into is Ubuntu again.  What do I need to do to be able to dual boot both Windows Xp and Ubuntu?  Thanks in advance guys.

---

### Post by frrobert on 2006-08-28
Here is link to fix your problem.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28dual%29%7C%28boot%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28dual%29%7C%28boot%29)


Moral of the story, if you are going to dual boot install windows first.  Windows wipes out the MBR for itself but ubuntu will look for other OSes

---

### Post by brainchild187 on 2006-08-29
Hey thanks for the reply.  That webpage indeed fixed my problem.  I am new to linux/ubuntu as of yesterday and the part I didn't understand was this:  

To GRUB, numbers begin with 0, and letters are expressed numerically, also beginning with 0.

For example, /dev/hda1 is "hd0,0" to GRUB. Similarly, /dev/hdb3 is "hd1,2".

after I knew that little titbit it was easy to fix the grub menu..... once again, thanks a lot.

---

