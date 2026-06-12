---
title: "The Disappearing Hard Drive"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Michael Hopcroft on 2007-05-28
I recently installed Fiesty on a system with two 250GB SATA hard drives. One of them is the system drive, which it's running on. The other one, which is where I backed my documents up before doing the install, seems to have vanished completely; I've succeeded in convincing the system that there is an sdb, but being able to locate it in the filesystem, or any of its contents, has been utter futility.

---

### Post by overdrank on 2007-05-28
> **Michael Hopcroft said:**
> I recently installed Fiesty on a system with two 250GB SATA hard drives. One of them is the system drive, which it's running on. The other one, which is where I backed my documents up before doing the install, seems to have vanished completely; I've succeeded in convincing the system that there is an sdb, but being able to locate it in the filesystem, or any of its contents, has been utter futility.

Hi you can use this command in the terminal *sudo fdisk -l* to locate the drive. And this *how to* will help you to mount the drive.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
Hope this helps and good luck! :popcorn:

---

### Post by sdbkr on 2007-05-28
Hi i have a similar problem with a second hard drive which i formatted with gparted to ext 3. i've followed the psychocats instructions at [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) 
i'm getting following in the terminal : 
name to write: /etc /fstab 
any idea what i should do ? press return, type in a name or a command ?

---

