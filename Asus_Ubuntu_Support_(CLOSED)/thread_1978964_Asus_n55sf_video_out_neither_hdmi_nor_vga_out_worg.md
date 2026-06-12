---
title: "Asus n55sf video out: neither hdmi nor vga out worgs in 12.04, any help?"
date: 2012-05-12
forum: Asus Ubuntu Support (CLOSED)
---

### Post by samuele.mattiuzzo on 2012-05-12
I all, i bought an asus n55sf and i've been so far happy with it, but now i need to configure the video outputs, and the situation isn't happy at all. With ubuntu 11.10 i tried installing bumblebee to enable nvidia and hdmi out, but that eventually turned out to be a bad idea. After a few weeks of not-working tries,i screwed up my entire computer. Only a dist-upgrade solved the problem, so now i'm on ubuntu 12.04 but stil i can't get hdmi nor vga out work. Any help? Vga-out would be great too,idon't mind at all! Video card is a geforce gt555m with 2gb and the integrated intel!  Thanks all!

---

### Post by monk0nuggets on 2012-05-23
I'm having this same issue.  It's because we haven't gotten a fully functional nvidia driver compatible with the Optimus chip.

---

### Post by p0l0us on 2013-01-30
I have same problem - no HDMI. 

nvidia 555M and I7 2670QM:
> 
 lspci -x | grep -i -e VGA -e DISPLAY
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF106 [GeForce GT 555M] (rev ff)

>  xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
LVDS1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080      60.0*+   59.9  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)


Bumblebee is working correctly (nvidia etc.)

Can anyone help ?

---

### Post by p0l0us on 2013-01-30
I found this solution:

[http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html](http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html)

It is not ideal, but it works on my N55SF !

edit:
It's good for watching movies and office work, but not usable for playing games. Keyboard responce is slow.

---

