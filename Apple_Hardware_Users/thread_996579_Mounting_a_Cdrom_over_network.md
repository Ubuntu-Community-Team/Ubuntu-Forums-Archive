---
title: "Mounting a Cdrom over network"
date: 2008-11-29
forum: Apple Hardware Users
---

### Post by Amerinidiot1231 on 2008-11-29
I cannot figure out how to mount a cd-rom over a network and I need to know because the cd-rom of my brothers computer is fried and I cannot get burning and mounting iso's to work correctly.  Help please!

---

### Post by jpkotta on 2008-11-30
Your question is vague.  What exactly do you want to do?

I will guess that machine A has a broken CD drive and you want files from a CD to get copied to it.  You have machine B with a working CD drive.  If both machines run Linux, on machine B:
```
sudo aptitude install openssh-server
sudo mount /dev/scd0 /cdrom
```
On machine A:
```
sudo aptitude install sshfs
mkdir mnt
sshfs *user*@B:/cdrom mnt
ls mnt

```

---

