---
title: "No sound from speakers on Asus 1015pem"
date: 2011-07-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by TimeSailor on 2011-07-11
[SIZE=2]Hello all,

I am new to Ubuntu. 

I have installed Ubuntu 11.04 on my Asus 1015pem, and for  some reason, my speakers will not work. Headphones work though. I have looked into the basic settings (I at least know mute isn't on, lol) but still no sound. Tried multiple scenarios, (i.e. Banshee music player, Youtube, etc.) so it doesn't seem to be an application issue. Weird thing is, speakers were working fine yesterday.

Any ideas? Thanks in advance for the help!

TimeSailor[/SIZE]

---

### Post by lidex on 2011-07-15
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

