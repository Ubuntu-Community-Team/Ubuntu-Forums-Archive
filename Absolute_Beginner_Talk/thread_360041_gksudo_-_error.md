---
title: "gksudo - error"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by KAL9000 on 2007-02-12
When trying to look in at my fstab to change the mount points and the like when following instructions to open the file I type 

"gksudo gedit /ect/fstab"

then the screen goes dark and it asks for my password.
after I hit return it opens a black "fstab" doc in gedit and gives an error in the termainal saying 

"(Gedit:4985) GnomeUI-WARNING **: While connecting to the session manager:
Authentication rejected, reason : None of the authentication protocals specified are supported and host-based authentication failed"

that looks abit extreme for a wrong pass word and I've had it several times now and I cant have got it wrong all those times.

If someone can help me with something else...what im acctualy trying to do here is make my /home dir on a new partition (as when I 1st instaled all Ubuntu is on one).

---

### Post by jvc26 on 2007-02-12
That error message is just a bug which has been reported but it isnt a problem you can ignore it.
Il

---

### Post by KAL9000 on 2007-02-12
But what ever it is its sopping me opening my fstab properly.

I know its not recomended but is there anyway of logging in as root so I can just open it :P

I wander is it possible to do direct deitingof the mount points, so if I dont want the partition to be in /media I can put it where I like just by editing the File path in that file?

any ideas on how to replse my home dir with a new partition and cpuy it all over seemlessly? 

I did manage to mount the new partition as /home/kal9001 wich didnt go down well as it replaced the one already there with 25GB of nothing.

If I mount it somewhere else. make a copy of the files over THEN remount it over?

but how to make the mount persistant through boot?

---

### Post by jvc26 on 2007-02-12
What is it stopping you doing? Is gedit not opening the file properly? The other question is, your initial code in your first post is wrong was that just a typo? As it should have read:
```

gksudo gedit /etc/fstab

```
Il

---

### Post by KAL9000 on 2007-02-12
Well Ive made a dir in / and mounted it no problem. BUT when trying to copy the contents of my /home folder over I dont have permitions to write to it. desipte that with I do:

cd /
ls -l 

It lists the dir1 that I made as "drwxr-xr-x" so i should beable to write to It. also using chmod and chown to change these say its not permited even when using sudo.

as I say cant I just login as root and have done with it :P

at least I have the drive mounted wich is the good thing. if i was smart i would have anticipated this and just partitiond the Linux half properly!

---

