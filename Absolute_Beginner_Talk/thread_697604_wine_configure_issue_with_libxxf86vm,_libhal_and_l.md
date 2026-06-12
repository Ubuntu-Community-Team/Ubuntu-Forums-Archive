---
title: "wine configure issue with libxxf86vm, libhal and libcapi20"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by darthshak on 2008-02-15
I downloaded the source package of wine 0.9.55 hoping that it will fix some directx issues i was facing (like the garbled AOM video problem of mine). I studied the how-to for compiling wine on 64 bit gutsy. However, when I ran ./configure, the symlinks worked for all but 3 libraries : 
```

configure: libxxf86vm development files not found, XFree86 Vidmode won't be supported.
configure: libhal development files not found, no dynamic device support.
configure: libcapi20 development files not found, ISDN won't be supported.

```

I realized that I must create symlinks to these libraries while compiling. So I did :
sudo mkdir -p 'pwd'/lib32 (in the wine tree)
I also did :
mkdir -p 'pwd'/lib32
ln -s /usr/lib32/libhal.so 'pwd'/lib32/libhal.so
ln -s /usr/lib32/libXxf86vm.so.1 'pwd'/lib32/libXxf86vm.so
ln -s /usr/lib32/libcapi20.so 'pwd'/lib32/libcapi20.so

However, I still ran into the same error. I even tried changing the file name in the synlinks but to no avail. Now, is there some sort of library incompatibility issue that I am not aware of with these libraries on 64 bit gutsy?

---

### Post by zvacet on 2008-02-17
Check in synaptic to see you have these libraries installed.If you don´t have them install.And if you can wait deb packages will be released very soon.I belive you know how to do it but still,just read [this.](http://www.winehq.org/site/download-deb)

---

### Post by darthshak on 2008-02-18
Yeah, I have the libraries installed....I even have them sitting in my folder

My guess is that they are not the right version or something. I also tried out the 32 bit versions, but no luck.
2 reason I dont want to do a .deb install :

a) I want to be familiar with how the whole thing works
b) Previously, I had done a .deb install of wine, but later on, when I compiled it with gcc, I realized that the previous install had some libraries missing from it. Compiling from source without hassles gives me the confidence that it will work.

Also, the issue I had with AOM was that the video was not resizing properly i.e. if Wine opened a 1440x900 window, the actual AOM screen was only 640x480. I figured that this was due to the lack of libxxf86vm functions as it is the library responsible for resizing windows.

So, I do need that library working fine. I also think that compiling with libhal is important as I had a weird issue with the pointer pointing to the wrong coordinates on the game menu as well.

---

### Post by darthshak on 2008-02-19
any idea when the .deb is coming out?

---

