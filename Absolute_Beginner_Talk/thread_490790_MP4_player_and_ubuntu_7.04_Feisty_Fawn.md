---
title: "MP4 player and ubuntu 7.04 Feisty Fawn"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by nowald on 2007-07-02
Hi!

I've been had problems with a mp4 player (USB), on my Ubuntu 7.04 distrib (I'm nowbie). The problems begins when I connect my mp4 player to the computer: the system block, and I can't do anything. If I try to disconnect the mp4 player from the USB, the system going down

I tipping dmesg on a Terminal, triying to know whats the problem. Here's the latest test resoult:
[http://paste.ubuntu-nl.org/26582/plain/]("http://paste.ubuntu-nl.org/26582/plain/")

So, I thought, that the problem was here:
```
[ 2149.542963]  sdb: unknown partition table
```

Thats why I tried to change the mp4's format (under win xp), to FAT32, but I still have the same problem

Any idea to solve it ? . Thanks


PD: my mp4 seems like that [http://maxmovil.com/datostienda/productos/833.jpg]("http://maxmovil.com/datostienda/productos/833.jpg")[ not spam, just an image to ilustrated what kind of mp4 player I have ] 

PD2: Sorry about my poor english   :neutral:

---

### Post by dwanders on 2007-07-02
It may be that your MP4 player is using MTP & PTP rather than USB mass storage. Use the following link to see if it helps you out at all

[http://en.wikipedia.org/wiki/Media_Transfer_Protocol](http://en.wikipedia.org/wiki/Media_Transfer_Protocol)

I have found most devices that use MTP (like my Samsung YP-TJ7 MP3 player) to sync files back and forth to the device don't work very well in Linux (or Windows for that matter - my experience has been weak at best with these MTP type devices). Most of the utilities listed can read the files on the device, but cannot manipulate them [edit, add etc...]. They may eventually (I am sure eventually they will) work fine, but for now I bet you would do better to try and stick with USB MSD based devices. You may consider checking the Hardware Comp list for devices prior to purchase to ensure it will work with Ubuntu:

[https://help.ubuntu.com/community/PortableDevices](https://help.ubuntu.com/community/PortableDevices)

Hope this helps.

---

### Post by nowald on 2007-07-03
Ok. Thanks you a lot ;)

I try to install the liib files(libmtp files and libgphoto files) and some programs (for example gnomad2), but I have the same problem. So, after read your post and wikipedia, I tried to use my old mp3 (64 MB - USB Mass Storage), and.....it works fine :p

Next time, I'll try to know if the device is absolutely supported by my OS before buy it . Thanks ;)

---

### Post by LELYLENCHO on 2008-06-28
> **nowald said:**
> Ok. Thanks you a lot ;)

I try to install the liib files(libmtp files and libgphoto files) and some programs (for example gnomad2), but I have the same problem. So, after read your post and wikipedia, I tried to use my old mp3 (64 MB - USB Mass Storage), and.....it works fine :p

Next time, I'll try to know if the device is absolutely supported by my OS before buy it . Thanks ;)


hello it is my first time using the Ubuntu, but i buy a mp4 device and came with a driver but i don't know where to find it ... can you tell me where the you find your device ?? thanks :)

---

