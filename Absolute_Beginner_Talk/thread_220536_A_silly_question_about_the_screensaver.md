---
title: "A silly question about the screensaver"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by UncleTally on 2006-07-21
Apologies if this is a silly question, but the screensavers that come with Ubunto are soooo slow? Why is this? Upon selection they run fine in the preview, but when they start they are painfully slow and jerky. My machine is pretty fast with plenty of RAM, so I cannot work this out. :confused:

---

### Post by trent dillman on 2006-07-21
It's probably your graphics driver...

what does ```
lspci | grep VGA
``` and ```
cat /etc/X11/xorg.conf | grep Driver
```tell you?

You may want to post your /etc/X11/xorg.conf here in it's entirety as well...

---

### Post by UncleTally on 2006-07-21
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 TurboCac he(TM) (rev a1)

and

 Driver          "kbd"
        Driver          "mouse"
  Driver        "wacom"
  Driver        "wacom"
  Driver        "wacom"
        Driver          "nv"

---

### Post by Lord Illidan on 2006-07-21
You have to install the binary nvidia drivers.

Do a ```
sudo apt-get install nvidia-glx
``` in the terminal.

---

### Post by trent dillman on 2006-07-21
You're using the non-3d accelerated 'nv' driver...
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by UncleTally on 2006-07-21
Thanks people, that worked a treat! :cool: 

What a fantastic community! :D

---

### Post by epb on 2006-08-30
I'm also having problems with my screensavers and tried the same commands as UncleTally did... I get

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]

Driver          "kbd"
Driver          "mouse"
Driver        "wacom"
Driver        "wacom"
Driver        "wacom"
Driver          "ati"

What do I do? Do I need a driver for my Radeon graphics card?

---

