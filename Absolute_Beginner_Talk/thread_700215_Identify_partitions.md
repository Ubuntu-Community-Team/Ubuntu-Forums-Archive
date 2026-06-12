---
title: "Identify partitions"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2008-02-18
Got a HDD with 5 partitions on it:

3 flavours of Windows on 3 partitions
Ubuntu on 1 partition
Linux swap on 1 partiton

(I think)

Anyway, want to reinstall the Ubuntu from the ground up. I've really smashed it up during the first 6 months of the learning curve.

My system works like this: Active partition is Ubuntu, menu.list has a final option to hand off to Windows Vista.

Vista's boot loader has it's own options to then select any of the windows stuff.

What I want to do is find a way of positively identifying each of my partitions so that when I reinstall from the Ubuntu or Kubuntu Alternate 64 bit CD, I can be sure of which partition to install to (so as to avoid damaging any of the windows installs)

Basically want to find out which partition is which.

what's the best tool to use to get that info.. & any suggestions for when I reinstall (any pitfalls?)

thanks. I can just about still use Ubuntu to post on here but it's not looking pretty:lolflag:

---

### Post by oedha on 2008-02-18
you can find out your structure by sudo fdisk -l
if you want to re-arrange the partition.....gparted - [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
if you want to repair the grub.....super grub disk

---

### Post by ecs_pf5 on 2008-02-18
Thanks :)

but.. oh dear

> 
user@ubuntu:~$ sudo fdisk -l
sudo: /etc/sudoers is mode 0777, should be 0440
user@ubuntu:~$ chmod 440 /etc/sudoers
chmod: changing permissions of `/etc/sudoers': Operation not permitted
user@ubuntu:~$ sudo chmod 440 /etc/sudoers
sudo: /etc/sudoers is mode 0777, should be 0440
user@ubuntu:~$ 



---

### Post by oedha on 2008-02-18
sudo chmod 440 /etc/sudoers

---

### Post by ecs_pf5 on 2008-02-18
Tried copy pasting it again but

```

user@ubuntu:~$ sudo chmod 440 /etc/sudoers
sudo: /etc/sudoers is mode 0777, should be 0440
user@ubuntu:~$ 

```

Seems as if, it's chicken and egg..

I know why it's doing this, I've run riot through the system changing permissions willy-nilly in the past.

I'm wondering whether to take a chance on it & just go ahead & boot up the Alternate CD for a reinstall. I'm scared that it will attack one of the Windows partitions though.

---

