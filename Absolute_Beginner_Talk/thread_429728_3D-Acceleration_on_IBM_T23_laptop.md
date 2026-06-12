---
title: "3D-Acceleration on IBM T23 laptop"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by sdahlinghwa on 2007-05-01
Hi,
   I'm new to Ubuntu/Xubuntu.  And I'm having a problem with 3D acceleration on my IBM T23 laptop which has an S3 SuperSavage/IXC16 3D capable video card built in - w/16MB memory.  
  General 3D acceleration - like screen saver's and such - worked just fine in Ubuntu/Xubuntu 6.10, but since I loaded Feisty Fawn (7.04) 3D doesn't work properly.  It's all choppy, as if 3D acceleration for the video card is not enabled.  And I don't know how to get the 3D to work again.  
   You would think that if it worked in 6.10 that it would also work in 7.04 - but it doesn't.  
   Does anyone know how to enable 3D acceleration for this video card in Xubuntu 7.04 (that's what I currently have on it)?  
   Or does anyone know if it's possible to use the 6.10 video card drivers in 7.04?
Please help.  


My system is as follows:
IBM ThinkPad, T23
Pentium III, 1133Mhz (mobile CPU)
768 MB Ram
S3 SuperSavage/IXC16 (16MB)
60 Gig Hitachi Hard drive

---

### Post by jsr on 2007-05-01
T23 and 3d accl? I really don't think that video card can do 3d acceleration. 
--
jsr

---

### Post by sdahlinghwa on 2007-05-01
It can't do new intensive 3D games and such but it's fine for general 3D - like for screen savers and such.  It used to run the 3D screen savers that come with Ubuntu just fine in 6.10 - however in 7.04 even the screen savers don't work.  That's not a problem with the video card, that's a problem with the drivers.

---

### Post by Cjames on 2007-05-04
I have the same laptop and the same problem. Hope someone can help with this.

---

### Post by K.B. on 2007-05-05
I also have upgraded to Feisty on my Thinkpad T23 and I was able to play TREMULOUS two days ago on it but since the upgrade I am getting the

[B][I]
Sys_Error: GLimp_Init() - could not load OpenGL subsystem[/I][/B]

error. 

I've been searching for what changed but haven't been able to find an answer anywhere.

---

### Post by haylocki on 2007-05-05
Hi,

     I'm not an expert, so probably can't help much, but I do have a T21 which I once got 3D acceleration working on. 

Gave up using it for 2 reasons :

1) cannot have 3D acceleration and 1400x1050 desktop, because of lack of video memory
2) Sooooo buggy, kept on crashing all the time.

Anyway, have you tried looking at the xorg log file ?

```
less /var/log/Xorg.0.log
```

Have a look for lines that start with (EE) as these show problems encountered when starting X

Check the default colour depth in xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

maybe the colour depth is too high so there is not enough memory, try changing it to 16 bit.

P.S. 

In case you don't know, a quick way to restart the X server is <CTRL><ALT><BACKSPACE>

You will need to log in again, but much quicker than rebooting. 


Cheers, Ian

---

### Post by K.B. on 2007-05-05
thanks for the tips... I did find a few EE items in that log:

> (EE) AIGLX error: dlopen of /usr/lib/dri/savage_dri.so failed (/usr/lib/dri/sava
ge_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering


(the other EE's refered to the lack of a Wacom pad or touchpad)

I tried changing the depth settings from 24 to 16 but it didn't help. 

this is where things go bad when I launch Termulous:

> ------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
Using 8/8/8 Color bits, 24 depth, 8 stencil display.
GL_RENDERER: Mesa X11


***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem


I tried what it suggests but it ran so badly I could see the screen refreshes...



---Added---  Just checked and  Planet Penquin Racer launches but the frame rate is horrible and makes it totally unplayable.

---

### Post by K.B. on 2007-05-06
I've been searching around for an answer to this problem but haven't found anything.


Is there any way to downgrade the graphics card drivers or at least part of them?

---

### Post by jackichad on 2007-05-10
I am experiencing the exact same problem on my T23 as well.  I had Ubuntu 6.06 loaded on it awhile back and never noticed this slowdown like I am now.

Would love to know a fix if anyone finds one.

Thanks!

---

### Post by K.B. on 2007-05-11
I've been searching around and have found references to this as a bug in Feisty and have tried a few things but nothing restores the pre-feisty programs back to what they were.

---

### Post by haylocki on 2007-05-14
Hi, Sorry for the delay.

looking at your error :

> 
(EE) AIGLX error: dlopen of /usr/lib/dri/savage_dri.so failed (/usr/lib/dri/sava
ge_dri.so: cannot open shared object file: No such file or directory)


it looks like your savage driver is missing, or installed in the wrong place

try typing :

```

locate savage_dri.so

```

on my T21 it returns

> /usr/lib/dri/savage_dri.so

if your system returns the file in a differnt location, try copying it to the same location as mine.

If no file is found you can try reinstalling the driver using synaptic

```
sudo synaptic
```

do a search for savage, and it should find the savage driver

then select mark for reinstallation

and apply

Cheers, Ian

---

### Post by aul2806 on 2007-05-16
I faced the same problem on my T23 laptop. Found solution for feisty at: 
[http://home.comcast.net/%7Ejyavner/T23/](http://home.comcast.net/%7Ejyavner/T23/)

Recompiling savage.ko and drm.ko solved my bug:

~$ glxgears
2094 frames in 5.0 seconds = 418.692 FPS
1991 frames in 5.0 seconds = 398.107 FPS

---

### Post by tirant on 2007-05-16
Same problem here:

```

$ cat /var/log/Xorg.log | grep AIGLX

(==) AIGLX enabled
(EE) AIGLX error: drmMap of framebuffer failed (Invalid argument)(EE) AIGLX: reverting to software rendering

```

Fix:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905/)

---

### Post by jackichad on 2007-05-17
To Aul2806 or anyone else who might be able to help:

I'm stuck when trying to follow the steps to enable direct rendering on my T23.  The instructions state:
```

* Install Debian packages "linux-source-2.6.18", "gcc", "libc6-dev", "linux-headers-2.6.18-4-686", and "linux-kernel-headers".
    * cd /usr/src/
    * tar jxvf linux-source-2.6.18.tar.bz2
    * cd linux-source-2.6.18
    * cp /boot/config-2.6.18-4-686 .config
    * make oldconfig && make prepare
    * cd /lib/modules/2.6.18-4-686
    * ln -s /usr/src/linux-source-2.6.18 build
    * Download this package to ~/drm.tar.bz2
    * cd
    * tar jxvf drm.tar.bz2
    * cd drm/linux-core
    * make DRM_MODULES=savage
    * mv /lib/modules/2.6.18-4-686/kernel/drivers/char/drm/savage.ko{,.old}
    * mv /lib/modules/2.6.18-4-686/kernel/drivers/char/drm/drm.ko{,.old}
    * cp {savage,drm}.ko /lib/modules/2.6.18-4-686/kernel/drivers/char/drm
    * depmod -a
    * Reboot
```

How do I go about completing the first step which says to install some Debian packages? Is that just done through Synaptic or is there more to it?

Thanks!

---

### Post by mbradlcu on 2007-05-17
I don't have this card but you may want to check this out:
daturan@matt-x64:~$ apt-cache search savage
xserver-xorg-video-s3 - X.Org X server -- legacy S3 display driver
xserver-xorg-video-s3virge - X.Org X server -- S3 ViRGE display driver
xserver-xorg-video-savage - X.Org X server -- Savage display driver

find out what package you have installed:
 dpkg -l|grep savage

maybe installing the legacy package may work.. hope this helps!


> **K.B. said:**
> thanks for the tips... I did find a few EE items in that log:



(the other EE's refered to the lack of a Wacom pad or touchpad)

I tried changing the depth settings from 24 to 16 but it didn't help. 

this is where things go bad when I launch Termulous:



I tried what it suggests but it ran so badly I could see the screen refreshes...



---Added---  Just checked and  Planet Penquin Racer launches but the frame rate is horrible and makes it totally unplayable.

---

### Post by haylocki on 2007-05-18
Hi, jackichad

To execute the first line you need to find out which kernel you are running :

```
uname -r
```

for example mine returns :
> 
2.6.20-15-generic

so for me the first line would be :

```
sudo apt-get install linux-source-2.6.20 gcc libc6-dev linux-headers-2.6.20-15-generic linux-kernel-headers
```

cheers, Ian

---

### Post by K.B. on 2007-05-19
Ian,

I followed your instructions since I have the same kernel
this installs  linux-source-2.6.20  rather then the linux-source-2.6.18  mentioned off that page.

I tried changing the command lines from the [http://home.comcast.net/~jyavner/T23](http://home.comcast.net/~jyavner/T23) to 20 instead of 18 but it doesn't work. 

Any ideas ?

---

### Post by K.B. on 2007-05-19
okay, I compiled the Savage drivers as per those instructions but used the location:
*lib/modules/2.6.20-15-generic/kernel/drivers/char/drm*

but it didn't change anything.  Still getting the same error when I try and run Tremulous.

---

### Post by haylocki on 2007-05-20
Hi,

are you still getting this error :

> (EE) AIGLX error: dlopen of /usr/lib/dri/savage_dri.so failed (/usr/lib/dri/sava
ge_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering 


or some other error ?

To see if your savage module is loaded try :

```
lsmod |grep savage
```

if this returns nothing try :

```
sudo modprobe savage
```

if the module loads ok try :

```
lsmod |grep savage
```

again.

It should return :

> savage                34048  0 
drm                     81044  1 savage

Cheers, Ian

---

### Post by jackichad on 2007-05-21
Just wanted to thank Aul2806 for pointing me in the right direction to fix the direct rendering problem and to haylocki for telling me how to execute the first line of the fix!  hehe

I now have 'direct rendering: yes' on my T23!!!  Here is my glxgears info:

2478 frames in 5.0 seconds = 495.481 FPS
2491 frames in 5.0 seconds = 498.170 FPS
2501 frames in 5.0 seconds = 500.147 FPS

Not sure how good those stats are but I can tell you that now my screensavers don't bring my machine to a crawl.

Thank you all again for the help!  I appreciate it so much!!!!!

-Chad

---

### Post by zenmor on 2007-05-24
oops.. i did not see it was a 3 page thread :)
fix seems to be here. thanks

---

### Post by aul2806 on 2007-07-04
I faced some problems with dri using google earth (computer freezes). Changing my /etc/X11/xorg.conf file like

#       Option  "BusType"               "AGP"
          Option  "BusType"               "PCI"

seems to solve that.

---

### Post by K.B. on 2007-07-04
I posted this in another 'Savage' thread but I know there's others out there with the T23 and this problem so I'm posting this solution over here as well:

I've been trying to get this to work on my T23 since I upgraded and I finally found the answer AND an easy one too!

check out this posting and when I did what he suggested and ran his installer it fixed everything and now my laptop says:

[B][I]
direct rendering: Yes[/I][/B]

[B]
follow this link to the message in the thread that helped me but check out the whole thread :[/B]
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905/comments/46]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905/comments/46")

---

