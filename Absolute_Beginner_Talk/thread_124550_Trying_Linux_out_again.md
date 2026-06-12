---
title: "Trying Linux out again"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by wee96 on 2006-02-01
Hello :) This forum seems to have some nice helpful people who dont get sick of us linux newbies asking questions, just what I needed. I've installed ubuntu on my system with an EVGA 6800GS (pcie), and of course the graphics are shot when X starts. Ive seen that I need the nvidia drivers. What exactly can I do from the command line to get the file? I know theres a text based web client but I cant remember the name, is there something simple that would be my best bet? I really want to use linux on my main system so I can use it consistantly. Thanks for any help.

-Dave

---

### Post by grimmson on 2006-02-01
I jsut found a post stating you may need to use "vesa" drivers to get a gui.

type "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak" to backup xorg
type "sudo vi /etc/X11/xorg.conf" scroll down until you find nvidia driver "nv" and replace with "vesa" write file "w" and quit "q". restart by typing "shutdown now -r" to reboot. 
if it doesn't work "sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf"
hunt me down and kick me. I think this will get you started to properly install new nvid drivers but I could be wrong. Good luck.

---

### Post by wee96 on 2006-02-01
Thanks for the help grimmson, ill give that a try.

---

### Post by David Corrales on 2006-02-01
One good text-based browser is Lynx. Get it by typing **sudo apt-get install lynx**.
Also, if you want to get accelerated performance from your video card, you can install the prepackaged nvidia drivers from the ubuntu repositories, it's the easiest way to do it. There's 2 drivers, regular (nvidia-glx) and legacy (nvidia-glx-legacy) which is meant for old GeForce 2 cards so you'll need the regular version. You'll also need to install the restricted modules for your matching kernel (which by the way, you should have either the 686 kernel for pentium machines or K7 for amd instead of the 386 which is the stock kernel).
The other way is to download the .bin file from nvidia, installing (apt-get) the kernel sources and compiler tools to build a module for your kernel.
Personally, I'd go with the prepackaged drivers. I just like being able to add/remove automatically.

---

### Post by wee96 on 2006-02-02
Thanks for the help guys, grimmson the vesa edit worked perfectly. I have a new problem though, I can only start an X session in root, if I try logging in with my other created user it errors out within 10 seconds with the following error:

mkdtemp private socket dir: permission denied

I've no clue what to do about that one.

---

### Post by wee96 on 2006-02-02
I reinstalled and it fixed that.

---

### Post by grimmson on 2006-02-05
Sorry for the late follow up. By now your running driver 8178 or so? If not to get the most current drivers just search the group for Howto nvidia.

---

