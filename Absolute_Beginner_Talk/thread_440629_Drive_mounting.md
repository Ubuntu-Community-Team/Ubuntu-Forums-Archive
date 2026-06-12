---
title: "Drive mounting"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Broken9754 on 2007-05-11
My two ntfs windows drives and a separate ntfs partition on the drive I currently have linux on aren't mounted by ubuntu. When I locate them under filesystem I get an error stating that there is no known application "for this file". They are located in /dev and are hda1, hdb1, and sda1. Any help in how to get them to mount and stay mounted? It's my understanding that they are read only by default in ubuntu, and I'm fine with that, but there is a lot of media on there that I'd like to be able to access. Thanks for any help.

---

### Post by BarfBag on 2007-05-11
[Automatix]("http://www.getautomatix.com/") has a tool that mounts all partitions and gives them write access.  If you don't want to use Automatix, [here's]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#Windows") instructions on how to do it manually.

---

### Post by Broken9754 on 2007-05-11
> **BarfBag said:**
> [Automatix]("http://www.getautomatix.com/") has a tool that mounts all partitions and gives them write access.  If you don't want to use Automatix, [here's]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#Windows") instructions on how to do it manually.

Perfect, thanks. Although at this point I'm going to shy away from giving myself write access. I can't be trusted.

---

### Post by Broken9754 on 2007-05-11
> **BarfBag said:**
> [Automatix]("http://www.getautomatix.com/") has a tool that mounts all partitions and gives them write access.  If you don't want to use Automatix, [here's]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#Windows") instructions on how to do it manually.

I spoke to soon. Trying to install manually I get:

david@david:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-config
david@david:~$

---

### Post by Broken9754 on 2007-05-11
> **Broken9754 said:**
> I spoke to soon. Trying to install manually I get:

david@david:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-config
david@david:~$

Nevermind, wrong link. Your way works great.

---

### Post by BHelts on 2007-05-11
do you have all repositories enabled?  --  nevermind.... just saw your post

---

