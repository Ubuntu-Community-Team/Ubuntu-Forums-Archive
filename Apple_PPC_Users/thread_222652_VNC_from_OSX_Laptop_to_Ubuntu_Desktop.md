---
title: "VNC from OSX Laptop to Ubuntu Desktop"
date: 2006-07-25
forum: Apple PPC Users
---

### Post by kapkorn on 2006-07-25
I have this setup using Chicken VNC on the OSX machine but it is REALLY slow but if I open Parallels on the Mac and use my Ubuntu VM and VNC that way it is fast. 


Is there a setting I am missing or does anyone know of a fix/better VNC client for OSX?

---

### Post by JonnyRo on 2006-07-25
I would check your color depth settings in Chicken VNC, make sure that you are not using higher than 16 bit color.

Also, you might want to try another VNC client.  You can even use tightvnc through darwinports. 

If you havent used darwinports before, check out [http://www.darwinports.org](http://www.darwinports.org)

You should download the apple compiler package from apple.com/adc (i think that link is right), before you get started with darwinports so you can have a compiler off the bat.

Unfortunately, the vnc clients from darwinports will probably need the Apple X11 stuff installed.

---

### Post by hotani on 2006-07-25
I had this problem too, and "fixed" it by upgrading the machine to AMD/ubuntu. ;)

I tried several different things with VNC but nothing would make the Mac as fast as another ubuntu box; not even close. I was using the OS X VNC client.

---

### Post by frafu on 2006-08-11
@hotani

What do you mean by "osx vnc client"? Where can I find it? 

Thanks in advance. 

frafu

---

### Post by hotani on 2006-08-11
I don't remember exactly which client I was using - I think it was [this one](http://www.versiontracker.com/dyn/moreinfo/macosx/9424).

---

### Post by frafu on 2006-08-11
Thanks for your reply; I did not understand correctly what you meant; I thought you were using a vnc client shipped with MacOSX... 

frafu

---

### Post by frafu on 2006-08-24
I can confirm that [VNCViewer]("http://homepage.mac.com/kedoin/VNC/VNCViewer/index.html") client 2.0.1 for MacOSX on my Mac works with the vncserver shipped with ubuntu desktop 6.06.1 i386.

frafu

---

