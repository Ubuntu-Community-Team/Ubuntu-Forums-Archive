---
title: "GNOME Shell is slow on MacBook Air 3,1"
date: 2011-01-01
forum: Apple Hardware Users
---

### Post by wersdaluv on 2011-01-01
I followed instructions on [https://help.ubuntu.com/community/MacBookAir3-2/Meerkat](https://help.ubuntu.com/community/MacBookAir3-2/Meerkat) , including the post install ones. Ubuntu with GNOME 2 runs fine, but some animations in GNOME Shell are very slow, like switching to and from Overview. 

I tried drivers from xorg-edgers and x-swat PPAs, but things are still slow. The most relevant solution I found is [http://live.gnome.org/GnomeShell/SwatList](http://live.gnome.org/GnomeShell/SwatList). I applied the patch 
```
$ cd ~/gnome-shell/source/gnome-shell
$ curl http://bugzilla-attachments.gnome.org/attachment.cgi?id=157326 > shell-animations-nvidia.patch
$ git am shell-animations-nvidia.patch
```

for nVidia performance, but things are still slow, which is weird because my other laptop with Intel X3100 runs Shell smoothly. 

Still trying to familiarize myself with Apple hardware, so I'd very much appreciate help. :)

---

### Post by wersdaluv on 2011-01-10
For some reason, it looks like the problem occurs only when some apps are running. So far, I noticed that Empathy, XChat, and software-center are among the culprits. 

Weird.

---

