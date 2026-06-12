---
title: "Fglrx gone bad"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by CommanderBob on 2008-01-24
I had compiz and the fglrx drivers working flawlessly with the cube and all. I wanted to set up vblank and antialiasing but after I entered sudo aticonfig --sync-vsync=on I got an Aborted Core Dumped error and now it says fglrx is not enabled and my computer is running extremely slow, even scrolling in firefox is super slow. I have a
FireGL V3100
1.5GB ram
Intel Pentium 4 3.2 GHz 
and a very slow computer...

Thanks,
Justin

---

### Post by CommanderBob on 2008-01-24
I just went to disable fglrx and it said 
"Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid or does not exist."
How do I get the X.org back? I had this problem before but I just reinstalled Ubuntu, I don't want to do that again.
Also I am using Ubuntu 7.10

---

### Post by CommanderBob on 2008-01-24
I just used sudo dpkg-reconfigure xserver-xorg to remake the x.org file and now I have the cool graphics and fglrx working but how do I get vblank syncing without using aticonfig?

---

