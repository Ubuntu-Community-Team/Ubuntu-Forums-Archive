---
title: "mount ntfs usb drive"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2008-02-20
I have just done a fresh install of Kubuntu gutsy

I tried plugging in an ntfs-formatted 160 Gb IDE hard drive, which is installed in obne of those usb caddy things.

I got the following error:

```

hal-storage-removeable-mount-all-options refused uid 1000

```

I tried a FAT-formatted usb stick, and that came up okay 

Is there something extra I need to do to see the contents of the NTFS drive in Kubuntu gutsy? From what I read on a search it should come up automatically but ISTR having to install some stuff in Ubuntu Feisty to get NTFS working.. bit confused :(

---

### Post by polmir on 2008-02-20
connect computer to internet and type in terminal
```
sudo apt-get install ntfs-3g
```
restart system and try connect USB disk with file NTFS

---

### Post by ecs_pf5 on 2008-02-20
Thanks :) seemed to already be there though :(

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 150 not upgraded.

```

Tried a search on Google (I spelled the error correctly this time - stupid me), now wondering if [http://ubuntuforums.org/showthread.php?t=601210](http://ubuntuforums.org/showthread.php?t=601210) might be the problem I'm running into.

---

