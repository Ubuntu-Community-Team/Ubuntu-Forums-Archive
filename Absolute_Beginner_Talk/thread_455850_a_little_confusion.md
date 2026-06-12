---
title: "a little confusion"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by lilro on 2007-05-27
here is my output for lspci:


```

00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.3 RAM memory: nVidia Corporation Unknown device 01aa (rev b2)
00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller (rev c2)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
01:07.0 Communication controller: 3Com Corp, Modem Division USR 56k Internal WinModem
02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)

```
earlier today, i was told to do this in order to get my graphics card to work:

```

sudo apt-get install nvidia-glx-legacy

```

i did that, and went to the restricted drivers manager to enable it. when i clicked to enable it, it removed nvidia-glx-legacy and installed nvidia-glx. here are the details:
```

(Reading database ... 112073 files and directories currently installed.)
Removing nvidia-glx-legacy ...
Selecting previously deselected package nvidia-glx.
(Reading database ... 112033 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1%3a1.0.9631+2.6.20.5-16.28_i386.deb)
...
Setting up nvidia-glx (1.0.9631+2.6.20.5-16.28) ...

```


so my question is if my graphics card is too old to be supported by ubuntu or not so i know if i absolutely *need* to buy another to play my games.

---

### Post by AAM on 2007-05-27
GeForce2 - hum, how old is that?

---

### Post by lilro on 2007-05-27
really old. like early 2000's. i have to use this because my family is strictly windows and they insist on using the newer computer.

---

### Post by lilro on 2007-05-27
bump

---

### Post by AAM on 2007-05-27
try this [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

---

### Post by AAM on 2007-05-27
and this - [http://ubuntuforums.org/showthread.php?t=434516&highlight=geforce2](http://ubuntuforums.org/showthread.php?t=434516&highlight=geforce2)

Additonal

the problem will be that the card is underpowered. but you may still get something going. My daughter uses a dual PII with a nVidia 5500 card and it works quite well. The minor problem was finding a PCI variant as they are disappearing fast (AGP still around, and PCIe ++++). You can find a better card fairly cheaply if you keep away from the 7000 series.

---

### Post by lilro on 2007-05-27
is the 7000 series bad?

---

### Post by RomeReactor on 2007-05-27
Hi. lilro, did the drivers install fine? what do you get from
```
glxinfo | grep direct
```

---

### Post by lilro on 2007-05-27
nope it didnt work. after i hit the gdm stop, and it went to the dos-like screen, i couldn't enter any thing

btw, i get this:

```

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

---

### Post by lilro on 2007-05-27
bump

---

### Post by hyper_ch on 2007-05-27
I had to use the legacy drivers for my old GeForce 2 GTS/Pro

---

### Post by lilro on 2007-05-27
how did you install it? can you give a brief walkthrough?

i enter:
```

sudo apt-get install nvidia-glx-legacy

```
and all goes well, until i try to enable it in Restricted Drivers Manager. it deletes it and install nvidia-glx

---

### Post by RomeReactor on 2007-05-27
Try running
```
sudo nvidia-glx-config enable
```
after installing the **nvidia-glx** dirvers (not the legacy).

It's odd that Ubuntu wants to install nvidia-glx instead of the legacy ones for that card...

---

### Post by hyper_ch on 2007-05-27
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by AAM on 2007-05-28
no, I was just thinking of the expense! The 5000-6000 series cards will do the job well and cheaply. If you are running a PCI interface (no AGP or PCIe), then you should start looking now, these cards are getting less common - though I expect eBay will do a good trade for some time.

---

### Post by lilro on 2007-05-29
ok thanks

---

