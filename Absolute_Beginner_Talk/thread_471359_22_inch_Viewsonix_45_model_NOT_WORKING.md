---
title: "22 inch Viewsonix 45 model NOT WORKING"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Brendan Hart on 2007-06-11
HAHA i did what i was told and it still didnt work,

went into Ubuntu in recovery mode and typed

spkg-reconfigure -phigh xserver-xorg and it came up with a bunch of drivers or something, i set it to vga at 1680 by 1050, and it came up with an error when i tried to reboot in regular ubuntu, i changed it to NV(assuming it was nvidia, and it worked but it came up with my old errors

Out of range
hfrequency 81
vfrequency 181

i could log in like when i heard a noise id type my user name press enter and then type password, then it would play the music signally it was loggin on, but i just couldnt see nothing.

---

### Post by taurus on 2007-06-11
Okay, this is what you should do.  Boot into recovery mode and reconfigure your X again.  

```
dpkg-reconfigure xserver-xorg
```
Use the default values and don't put in the horizontal and vertical refreshing rates, yet.  Use nv for now.  Save it and reboot.

Once you get X running, install nvidia driver for your graphic card and then go to the high resolution, 1680x1050, after you have installed nvidia driver for your graphic card.

[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by Brendan Hart on 2007-06-11
Um when i typed it in earlyer on my computer (with the -phigh ) it didnt give me any options cept a bunch of video cards and resolution after i selected my video card. Also we are operating linux, how do i install my nvidia card with a windows cd, i dont have internet on my computer, look in my other thread to help me decide what wireless card i should get with least nightmares installing and powerful

---

### Post by sonofusion82 on 2007-06-11
you can download the deb package to install the nvidia driver.

---

