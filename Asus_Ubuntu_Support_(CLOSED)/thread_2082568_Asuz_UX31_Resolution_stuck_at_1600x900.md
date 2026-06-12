---
title: "Asuz UX31 Resolution stuck at 1600x900"
date: 2012-11-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Loan_Refi on 2012-11-09
Hello,

I need help changing my resolution from 1600x900. I open my display settings and the only option available is 1600x900.

My system:
Asuz UX31 Ultra Slim
Linux 3.2.0-33-generic x86_64
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"

Output of glxinfo | grep OpenGL
$ glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 3.0 Mesa 8.0.4
OpenGL shading language version string: 1.30
OpenGL extensions:

lspci | grp VGA Output
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

xrandr Output
~$ xrandr -q
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192
eDP1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 293mm x 164mm
   1600x900       60.0*+
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
 
Anyone has any ideas on how I can get a lower resolution. My eyes are getting tired with the small text etc.

---

### Post by 2F4U on 2012-11-10
I don't know the native resolution of your display, but modern screens have an optimal resolution and deviating from it usually makes things worth. What about changing the DPI settings to make fonts larger?

[https://wiki.ubuntu.com/X/Troubleshooting/HugeFonts](https://wiki.ubuntu.com/X/Troubleshooting/HugeFonts)
[http://www.upubuntu.com/2012/05/how-to-change-font-and-ui-user.html](http://www.upubuntu.com/2012/05/how-to-change-font-and-ui-user.html)

---

### Post by Loan_Refi on 2012-11-10
Hi, thanks for pointing out the two options. The first one helps for now. I totally forgot about and my eyes are starting to feel better! However the problem remains. 

The truth is the display dimension is correctly set at 1600x900. The problem is that I'm getting too old to see the nice small define font. What I want is a lower resolution such as a 1366x700 I think. 

The problem is that the display settings only have 1 setting, 1600x900. I want to have the option to go lower like I did on previous version of Ubuntu. 

I use remote desktop a lot and even though you help me increase the font size on my Ubuntu system I still have small fonts on the remote desktops I connect to. 

Here's an example of my system vs remote desktop;

---

