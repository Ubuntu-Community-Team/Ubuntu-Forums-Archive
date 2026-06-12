---
title: "ATI [9200SE] Driver"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2007-01-07
After my Readon 9800pro burned, I placed an old 9200SE in my computer.
I reinstalled Ubuntu to make sure everything works, and now I am trying to install the damn ATI drivers.

First I tried this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29)

And after reboot it still shows as
```
aktiwers@Hal:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

Then I went to ATI and downloaded the drivers manually here:
[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)

And follows this guide:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8-inst.html)

But still it shows MESA and not ATI in the fglxinfo?

I tried to reconfigure xserver - but it stills shows MESA?

Then I run dmesg | grep fglrx:
```
aktiwers@Hal:~$ dmesg | grep fglrx [17179607.076000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179607.080000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179607.080000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179611.912000] [fglrx:firegl_unlock] *ERROR* Process 4633 using kernel context 0

```

Anyone knows what I am doing wrong here? and what that error means?
I want 3d support so I can use OpenGL.

Thanks a lot!

---

### Post by aktiwers on 2007-01-07
Also my Fps is extremely low:
```
aktiwers@Hal:~$ glxgears -iacknowledgethatthistoolisnotabenchmark 607 frames in 5.2 seconds = 116.763 FPS
684 frames in 5.7 seconds = 119.418 FPS
684 frames in 5.6 seconds = 122.362 FPS
684 frames in 5.7 seconds = 120.144 FPS
```

---

### Post by smoker on 2007-01-07
hi, maybe i was lucky, but i have the 9200se and i never had to install any other drivers, it just worked. also 3d just worked, and have just installed beryl with no probs.

did you check if you need to adjust your graphics card in your bios?

---

### Post by aktiwers on 2007-01-07
When I go to Start=>System=>Administration=>Device Manager
It show it identify my ATI Card..
Maybe its because you are on Edgy and im on Dapper?

What about the error messege I recieve? Maybe thats what needs to be fixed?

---

### Post by smoker on 2007-01-07
i have dapper on another partition though, and never had probs with that either.

sorry i can't help with the error message, linux isn't that deeply engrained yet. i'm sure someone will have some suggestions though.

---

### Post by aktiwers on 2007-01-07
/bump

---

### Post by ffxr on 2007-01-09
i have just worked my way through the same problem with an ATI 9200SE also...

first make sure.. that your using the ATI driver version 8.28.8

any later version will not work with the ATI9200 card...


[B]do these: (doesnt matter if youve already done them)
[/B]
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

modprobe agpgart
modprobe -r fglrx
sudo gedit /etc/X11/xorg.conf

**add/change the items in red (leave any other entries alone!!!) to your graphic card section and SAVE it:**

Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
[COLOR="Red"]Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "UseInternalAGPGART" "no"[/COLOR]
EndSection

[B]
Add these lines to your /etc/modules and SAVE it: [/B]
agpgart
fglrx
dri

**Make links to your dri modules:**
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri


**reboot**
it is essential to reboot and not just restart x in this instance..


good luck.!

---

### Post by aktiwers on 2007-01-10
Thanks I will try it out tomorrow when Im done with my Examen.. or I mean Friday, when im not drunk anymore ;)

Btw, I reinstalled Ubuntu and im now on Edgy(instead of dapper), it seams to have 3d support out of the box, but my FPS is still very low..

As I said, I will try this on friday, though I did try it on dapper without luck..

But thanks again, I will post the results :)

---

