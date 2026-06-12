---
title: "Beryl issues pertaining to Desktop effects."
date: 2008-01-03
forum: Apple Intel Users
---

### Post by ianoreo on 2008-01-03
I used [http://www.arsgeek.com/?p=1313](http://www.arsgeek.com/?p=1313) as a guide after I installed Ubuntu onto my MacBook with parallels because I really wanted Beryl. When I go to enable Desktop effects a white screen comes up and I hit escape and it goes away. The enabling doesn't occur but every time I retry the same thing happens. I decided I would skip that part and carry on with the tutorial. Suddenly, at the end, there was an error to the Beryl installation that said that something in me driver was screwed up and I had to erase the VM.

I am new to Ubuntu so please be easy on me with the jargon :D

Ian

---

### Post by alephsmith on 2008-01-03
You will not be able to use Beryl (or any 3d compositor) in a Parallels virtual machine.

This is because there is no 3d acceleration in the video drivers used in parallels.

You will need to install a full blown Ubuntu system on your HDD to get the benefits of a 3d desktop with beryl or compiz.

---

### Post by ronocdh on 2008-01-03
> **alephsmith said:**
> You will not be able to use Beryl (or any 3d compositor) in a Parallels virtual machine.

This is because there is no 3d acceleration in the video drivers used in parallels.

You will need to install a full blown Ubuntu system on your HDD to get the benefits of a 3d desktop with beryl or compiz.
I had read that Parallels 3 [added 3D acceleration]("http://www.parallels.com/en/products/desktop/features/3d/"). Does this for some reason only apply to Windows?

---

### Post by macaholic on 2008-01-04
> **ronocdh said:**
> I had read that Parallels 3 [added 3D acceleration]("http://www.parallels.com/en/products/desktop/features/3d/"). Does this for some reason only apply to Windows?
That is what i have heard as well, that the 3d acceleration only pertains to windows, not sure why, but I would guess that it is theoretically possible if you messed around in the xorg file enough.

---

### Post by cyberdork33 on 2008-01-04
> **ronocdh said:**
> I had read that Parallels 3 [added 3D acceleration]("http://www.parallels.com/en/products/desktop/features/3d/"). Does this for some reason only apply to Windows?
Yep it supports certain directx calls. VMWare also supports this (up to experimental support of DirectX9 now.

Parallels does claim it can use OpenGL though, which indicates it should be possible to get some 3d rendering in linux, but I have not heard of anyone getting it working. You might try checking the parallels forums: [http://community.parallels.com/forum/](http://community.parallels.com/forum/)

---

