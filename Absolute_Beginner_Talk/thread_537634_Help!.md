---
title: "Help!"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by bryman on 2007-08-29
I tryed to install ubuntu dual boot with vista (following the many guides online) and everytime i got to the end of the install it asked me to take out the disk and press enter. However it did not react to my pressing :( and when i rebooted, it just got past the GRUB loader and black screened :( so after many attempts i using the different the two different versions i decided to install it on its own on the whole drive, i used the text installer this time aswell. It installed fine and this time restarted properly but it again posts to a black screen after the the GRUB menu. What am i doing wrong, I cant find an answer anywhere :(

---

### Post by hyper_ch on 2007-08-29
well, is the screen totally black or do you get any error message?

For the next thread - use a more descriptive title... everybody (or almost) who opens a topic here asks for help.

---

### Post by bryman on 2007-08-29
no error message :( just a black screen. It pass's the bit that says loading kernal. Then there are a few flashs's but then just plain black :( but the monitor is still recieving a signal. If i load it in the recovery mode its gets so far then says "root@bryan:" 

thanks for the advice :)

---

### Post by hyper_ch on 2007-08-29
hmmm, with the desktop cd you actually had Ubuntu running in ram?

---

### Post by bryman on 2007-08-29
when i use the desktop cd it loads fine and i can run it off the cd but after i have installed it i get the same problem :( im running a C2C Duo E6300, 2GB Geil Ultra 6400 RAM, 8800 GTS 640MB and a 500 GB Seagate hardrive

---

### Post by hyper_ch on 2007-08-29
From the German site here do this: [http://blog.ikasweb.de/2007/05/29/geforce-8800-gts-mit-ubuntu-704/](http://blog.ikasweb.de/2007/05/29/geforce-8800-gts-mit-ubuntu-704/)

(1) Run recovery mode (your are root there as I see from your previous example)

(2) Run this:

```

apt-get install linux-restricted-modules-generic

```

(If you are not root, you need to prepend that command with "sudo")

(3) Then run this:

```

apt-get install nvidia-glx-new

```

(4) Get the latest drivers off the nVidia page:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Use the IA32 for a 32bit processor
Use the IA64 for an Intel 64bit processor
Use AMD64 for AMD 64bit processor

(5) Unpack that file
```

sh NVIDIA-Linux-x86-100.14.11-pkg1.run -x

```
Of course replace that with the actualy file name ;)

(6) Copy it to the right location:
```

sudo cp -f NVIDIA-Linux-x86-100.14.11 -pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so /usr/lib/xorg/modules/libwfb.so

```

(7) Run nvidia config
```

sudo nvidia-xconfig

```

---

### Post by bryman on 2007-08-29
when i type step three i get this message.

Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package nvidia-glx-new has no installation candidate
root@Bryan-Desktop:~#

---

### Post by hyper_ch on 2007-08-29
Hmm, I guess it's then in some repos you haven't got enabled yet.

Use the sources list generator:  [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

The only ones I haven't installed from there are those:

Kubuntu.org bleeding edge KDE  
Kubuntu.org bleeding edge Koffice  
Kubuntu.org bleeding edge amaroK  
Upstream Beryl  

After you have replaced the sources list ( /etc/apt/sources.list ), you should also run the keys as it is said in the generated list.
```

sudo apt-get update

```

Then you can try again.

---

### Post by bryman on 2007-08-29
How do i replace the sources list "confused" :(

---

### Post by hyper_ch on 2007-08-29
you need to edit it

---

### Post by bryman on 2007-08-29
if i type startx at the root@bryan i can get to the desktop but where do i go from there?

---

