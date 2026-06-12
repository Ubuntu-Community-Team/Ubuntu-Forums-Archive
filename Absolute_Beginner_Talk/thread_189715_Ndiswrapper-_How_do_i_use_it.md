---
title: "Ndiswrapper- How do i use it?"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by FlyingPenguin on 2006-06-05
So I come from SUSE where I use the ndiswrapper command and modprobe to make my WLAN card work. How do I use ndiswrapper in Ubuntu? I was sure it comes with it, but i type ndiswrapper at the terminal and get nothing (bash command not found).

What do I do?

---

### Post by joshrobinson on 2006-06-05
[QUOTE=FlyingPenguin]So I come from SUSE where I use the ndiswrapper command and modprobe to make my WLAN card work. How do I use ndiswrapper in Ubuntu? I was sure it comes with it, but i type ndiswrapper at the terminal and get nothing (bash command not found).

What do I do?[/QUOTE]

the best thing to do is compile it from source-code
grab the ndiswrapper .tar from their sourceforge website

use synaptic to install your kernel headers and build-essential
then go into the directory of ndiswrapper after you extract it from the tar

```
sudo make distclean
sudo make install
```

then you can run your modprobe, depmod and rrmod commands
that will make sure to get you the newest version

but if you dont mind using an older version, you can take the easy way out

```
sudo apt-get install ndiswrapper-utils
```
and that will install it for you

---

