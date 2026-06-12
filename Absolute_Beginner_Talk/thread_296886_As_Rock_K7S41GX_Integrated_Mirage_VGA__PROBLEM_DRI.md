---
title: "As Rock K7S41GX Integrated Mirage VGA  PROBLEM DRIVER"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by mr_manson on 2006-11-10
HI to ALL

I've this MB As Rock K7S41GX with Integrated Mirage VGA adaptor

...i think sis chipset 

but...i can't change the resolution fron 1280 x 1024 when I try to change to 1024 x 768 the system go in "crash" and after few second...the logon window appears and i can logon again....but only 1280 x 1024 

Does anyone help me ...exist or not some driver  ? :mrgreen:

---

### Post by angryfirelord on 2006-11-10
Open a terminal and type: *sudo gedit /etc/X11/xorg.conf*

Scroll through the crazy text until you hit a section titled **Section "Device"**

Go down to where it says **Driver** and change it to say **"vesa"**

-What I just did is told the computer to use the generic driver instead of another driver.

Now under **Section "Screen"** look for the **DefaultDepth**. Go to the **SubSection "Display"** that has that depth. (ex. I have it set to 24 so look for the SubSection that has Depth at 24).

Under **Modes** add "1024x768" (with the quotes). If you don't want 1280x1024, you can get rid of that too. 

Do a reboot and you should be ok.

Now if that seemed a little complicated, or if it crashed, you can always do a **sudo dpkg-reconfigure xserver-xorg** and use the defaults except for display driver and video mode (use vesa and 1024x760).

---

### Post by mr_manson on 2006-11-10
THANKS A LOT THANKS A LOT THANKS A LOOOOOOTTTTT  :mrgreen: :KS

---

### Post by angryfirelord on 2006-11-10
hey no problem!

the problem with the other drivers is that they're a little funky at times. I had an issue with Ubuntu on an older machine which had a Radeon 7000 video card and it would give me a black screen every time I started it up. Setting it to vesa fixed the problem.

If you do get into Ubuntu more, I'm sure you'll want to play some of the 3D games that are out there. 3D doesn't happen on SiS onboard video in Linux. :) 
I recommend plugging in a cheap-o nVidia card to get some 3D support! Unless you play games at high resolutions, an MX4000 will do fine for most of the freebie Linux games out there: [http://www.newegg.com/Product/Product.asp?Item=N82E16814130198]("http://www.newegg.com/Product/Product.asp?Item=N82E16814130198")

If you do decide to get it, you must install nvidia drivers, which is easier than Windows drivers. In Synaptic, look for nvidia-glx and install it, or go to a terminal and type **sudo apt-get install nvidia-glx**. Use either dpkg-reconfigure to set it to nvidia driver or change the Driver to "nvidia". 

Happy Ubuntu-ing! :D

---

