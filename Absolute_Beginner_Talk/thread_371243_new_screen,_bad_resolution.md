---
title: "new screen, bad resolution"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by smartalecks on 2007-02-26
I just got a Sceptre 20.1" Wide Screen monitor up from an old 17" Trinitron CRT (<3). Its great and seems to have been detected fine but the resolution is still set at 1280x1024, but there is not option for a higher resolution under System>Preferences>Screen Resolution.

I have the latest nvidia beta drivers installed and working well, as well as Beryl set up. I'm wondering if I can work this out without killing these.

thanks

Ubuntu Edgy Eft 6.10

KT600 Dragon Ultra
1024 MB RAM
AMD Athlon 2800 XP @ 2.1 ghz

nVidia GeForce FX 5500 (256mb)

---

### Post by johnc4510 on 2007-02-26
You can reconfigure x by using the following command in a terminal, Please note that I don't know what this will do to Beryl, but part of the reconfigure will allow you to set your resolution.
sudo dpkg-reconfigure xserver-xorg

---

### Post by ed-j on 2007-02-26
LCD or TFT monitors have a "native resolution" ( in other words, only one with which they will work properly ). When you try other settings, you will get something like "program not supported".

However, the x-server may support your resolution?

All the best!

---

