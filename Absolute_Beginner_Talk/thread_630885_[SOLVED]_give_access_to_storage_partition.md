---
title: "[SOLVED] give access to storage partition"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by TheTeZ on 2007-12-03
when i installed kubuntu i made 3 partitions.  a 4 gig+ partition for the install directory... sort of like a C drive in windows.

i created the swap partition. a gig or something

i created a 14 gig storage partiton that i wanted to use to store my files.... music, etc. 

when ever i try to save to the partition hda3 it says i dont have access....  how do i grant access to this device... i have tried sudo chmod 777 media:/hda3 and it said that the folder couldent be found,... 

i hope this is a simple fix... im sure it is ... but im pretty new to linux.

---

### Post by xinix111 on 2007-12-03
the drive might have other permissions than root, if its your username, than root can't acces, without sudo you should be fine ((aswell you might just log in as user andad a disk mounter to your panel and mount the drive as user, after that you change the permissions to root)),

---

### Post by TheTeZ on 2007-12-03
it says ownership and group are root...

and what is / how do i add a disk mounter

---

### Post by fenian on 2007-12-03
Use these commands...

> sudo chown -R user:user /storage
sudo chmod -R 755 /storage

Replace user with your username and /storage to the path of your partition.

---

### Post by TheTeZ on 2007-12-03
thank you. that worked. what does 5 give me?

---

### Post by xinix111 on 2007-12-03
rightclick your panel and choose add, search for diskmounter, but the commands were quite a good suggestion too

---

### Post by fenian on 2007-12-03
755 gives read write access  to the owner which was set with the chown command.

---

