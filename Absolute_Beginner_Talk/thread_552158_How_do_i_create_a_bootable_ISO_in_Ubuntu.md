---
title: "How do i create a bootable ISO in Ubuntu?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by DAE_JA_VOO on 2007-09-16
Hi there guys

I've searched the forum and didn't find anything :(

I have got an Ubuntu Gamer's Edition disc, and i need to make an ISO of it so that i can write it for a friend, but i don't know how to make the ISO. 

I need a program to do this (IN Ubuntu), any suggestions?

Thanks guys :)

---

### Post by Crafty Kisses on 2007-09-16
You probably want to use a program called "k3b" it can burn ISO's.

```
sudo apt-get install k3b
```

---

### Post by DAE_JA_VOO on 2007-09-16
Hmmm... k3b seems to be able to do everything except CREATE ISO files. I have the Bootable DVD in my drive, i need to CREATE the ISO first, then burn it...

---

### Post by Malta paul on 2007-09-16
K3b is great, you might like to also check out [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
Have fun :)

---

### Post by Crafty Kisses on 2007-09-16
> **DAE_JA_VOO said:**
> Hmmm... k3b seems to be able to do everything except CREATE ISO files. I have the Bootable DVD in my drive, i need to CREATE the ISO first, then burn it...

K3B, is really made for creating ISO's files, haha, look closer. :)

---

### Post by mikewhatever on 2007-09-16
Since you want to copy the CD, choose the copying option. In the process, an iso file created and then written to a cd.

---

### Post by Crafty Kisses on 2007-09-16
> **mikewhatever said:**
> Since you want to copy the CD, choose the copying option. In the process, an iso file created and then written to a cd.

Exactly. :)

---

### Post by armandh on 2007-09-16
An iso file is one that can restore the files it contains to the original arrangement.
To be bootable the iso file must contain an OS and boot loader
From an iso file to a CD in 7.04 I just right mouse button on the file and select write to disk. 
You mention using a DVD.
I do not know if an iso file for a CD will write correctly to a DVD
If you want a self booting disk with a program on it you need an live OS as well as the application on the disk.
I have never done this but a good example is parted magic.

---

### Post by DAE_JA_VOO on 2007-09-16
Thanks guys, closer look at k3b got me doing exactly what i needed. Thanks guys :D

---

