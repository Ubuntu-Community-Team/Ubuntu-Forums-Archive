---
title: "OSS Installation?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by heyniceaddress on 2008-03-08
(I am installing this as I have no sound, and I have tried many attempts at fixing it to no avail; after doing some research, however, I found that it is most likely due to the fact that my Dell has a Sound Blaster X-Fi installed, and ALSA does not support it; recently, though, OSS developed a file that may fix it, and that's why I'm here asking you all.)

Can anybody explain to me which of the files I need to download from this site and how to go about installing it? I do not know enough yet about Linux/Ubuntu to understand even which file will work with 7.10 and how to go about installing it. Thank you in advance:

[http://www.opensound.com/index.html](http://www.opensound.com/index.html)

Here are my system specs that somebody asked for before:

*-multimedia UNCLAIMED
description: Multimedia audio controller
product: SB X-Fi
vendor: Creative Labs
physical id: 4
bus info: pci@0000:05:04.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list
configuration: latency=64 maxlatency=5 mingnt=4

---

### Post by herbster on 2008-03-08
Ubuntu comes with OSS, AFAIK, though I might be wrong.

---

### Post by heyniceaddress on 2008-03-10
This file was just recently released for people who share the same problem as I do with Ubuntu; I found it after reading similar problems with others who have Sound Blaster X-Fi cards like me. I still am uncertain which file to download and how to go about installing it.

---

### Post by herbster on 2008-03-10
[http://www.4front-tech.com/release/oss-linux_v4.0-1014_i386.deb](http://www.4front-tech.com/release/oss-linux_v4.0-1014_i386.deb)

That's the install you would download. Just save it to your Desktop and double-click it, proceeding with the installation. It's similar to a .msi/.exe installer from Windows.

---

### Post by heyniceaddress on 2008-04-04
Much obliged! Finally I have sound and am able to enjoy Ubuntu fully.

Thank you!

---

