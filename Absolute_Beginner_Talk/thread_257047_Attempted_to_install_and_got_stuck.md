---
title: "Attempted to install and got stuck"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2006-09-14
Hi!  I keep getting stuck at the partitioning.  I can't select the option to have Ubuntu resize the current first partition, because it fails (understandably so, because that is my HP recovery partition).  Is there any way that I can get it to look at the second, correct partitiion instead?  I just can't do partitioning work myself (I am too newish to linux).  Thanks!

---

### Post by Darklighter137 on 2006-09-14
I'm not sure if bumping is aloud here, but I am going to do it anyway since  I appear to be the only one that has looked at this thread (I timed the posting poorly--you guys are the best and have helped a lot). ^_^

---

### Post by CatKiller on 2006-09-14
I can't remember that much about the Ubuntu install process, since I only had to do it the once, quite a while ago now. But FWIW the partitions are numbered hda1 for the first partition on the first hard disk, hda2 for the second, and so on, and hdb1 for the first partition on the second hard drive, hdc1 for the first partition on the third drive, and so on. Perhaps this will help you to find the correct partition to try to install on.

Isn't there a "use the largest free space" option or something? It's all so hazy. Sorry I can't help you more.

---

### Post by K.Mandla on 2006-09-14
If I understand you right, you might want to look into a live CD of GPartEd, which would allow you a little more freedom with partitioning. It's not nearly as complicated as it might sound -- it's basically a graphical setup, but with a better level of control since it boots into a live environment. I don't know if that will help, but I thought I would mention it. ;)

---

### Post by Darklighter137 on 2006-09-14
To poster number 1:  No, it wants to use the free space from the first partition, which is a FAT32 recovery partition put on there by HP.

To poster number 2:  So, what would be the advantage of doing that versus simply partitioning during install?  Am I wrong in thinking that uses GParted?  The main problem I have is that this is my first time installing linux AND my first time partitioning. =(

---

### Post by xpod on 2006-09-14
you can use the gparted app ON the ubunto live cd to do your partitioning first prior to begining the install procedure.

That way you get a better idea of what your creating as you can see it all

---

### Post by Darklighter137 on 2006-09-14
Hmm, can I just halve my NTFS partition, and the let the installer use that as it sees fit?

---

### Post by xpod on 2006-09-14
defrag defrad defrag your windows first

---

### Post by Darklighter137 on 2006-09-14
Okay. ^_^

---

### Post by K.Mandla on 2006-09-14
> **Darklighter137 said:**
> So, what would be the advantage of doing that versus simply partitioning during install?  Am I wrong in thinking that uses GParted?  The main problem I have is that this is my first time installing linux AND my first time partitioning. =(
My fault; I misunderstood your description. #-o Cheers.

---

### Post by Darklighter137 on 2006-09-14
That's fine--I misunderstood the installer! =P

---

