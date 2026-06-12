---
title: "Nvidia-drivers install"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by achtungbaby on 2006-03-05
I've recently downloaded and installed Ubuntu on my computer. I'm an experienced Windows user and have during the last year been looking for an alternative OS instead of the old and slow XP.

When I used Mandrake I experienced some weired resolution problems. I couldn't get resolutions above 1024x768. I prefer 1280x1024 and working with other resolution is not an option for me really. I tried to change the xorg.conf-file in mandrake with the correct Vertical and Horizontal sync-rates but it didn't work.

Now, I've got the same problem with Ubuntu. I've set the sync-rates according to the manual but stil I can't use my prefered resolution.

As a windows user the first things that always comes up is that I need some drivers. I got the latest drivers from nvidia.com and tried to install. The installation program then said that there is no pre-compiled version for my kernel so the drivers needs to be compiled. I've downloaded the source for my unix kernel:

```
otto@stat:~$ uname -r
2.6.12-10-386
```

from [http://www.kernel.org/](http://www.kernel.org/). I used the linux-2.6.12.tar.bz2-file and decompressed into /usr/src/. The I made the a link with:

```
otto@stat:~$ sudo ln linux-2.6.12 linux
```

When I run the installationprogram for the nvidia drivers it complains about the file: /usr/src/linux/include/linux/version.h. The problem is that the file doesn't exist!

Please help me to fix my resolution problem!

---

### Post by knalle on 2006-03-05
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+howto](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+howto)

---

### Post by achtungbaby on 2006-03-05
[QUOTE=knalle][http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+howto](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+howto)[/QUOTE]

I've tried this but the when I run:

```
sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`
```

it says that nvidia-settings is not available. Which I guess means that there's now precompiled version for my kernel. :(

---

### Post by knalle on 2006-03-05
obs, i think that means you haven't enabled **multiverse**, read the beginning on the how-to about adding **multiverse** to our repositories.

happy hacking

---

### Post by achtungbaby on 2006-03-05
No, all my repositories are multiverse, except for the CD-repository with Ubuntu Breezy Badger.

---

### Post by achtungbaby on 2006-03-06
Now it works fine. I downloaded EasyUbuntu. 1280x1024 works perfect!

---

