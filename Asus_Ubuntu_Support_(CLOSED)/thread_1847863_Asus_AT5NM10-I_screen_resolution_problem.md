---
title: "Asus AT5NM10-I screen resolution problem"
date: 2011-09-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Miguelbu on 2011-09-21
[SIZE=2]Hi Guys, new to the forum and not the best Linux user, but tired of windows...

I'm having a screen resolution issue in my Asus[/SIZE][SIZE=2] AT5NM10-I motherboard.[/SIZE][SIZE=2]


I Cannot have **1280x1024 **resolution.. tried xrandr and so one.. didn't tried to change xorg.conf because dont know what to do...

What to do?:confused:

Tanks in advance

[/SIZE][SOLVED]
Solution:

My main problem was that the code mode dind't have the same name

SO:

1ºCommand
```
xrandr --newmode "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```
2ºCommand
```
xrandr --addmode VGA1 1280x1024
```

"1280x1024" is the name You want to give him (U can actually call it what ever u want)

AND NOT:

```
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```
 2ºCommand
 ```
xrandr --addmode VGA1 1280x1024
```

If U Want to Use in command 1º the name of the mode "1280x1024_60.00" in command 2º it must have the same name.

Also Instead of copypaste the code from forum I did:

```
cvt 1280 1024
```

Use This code To generate part of 1º Command instead of copypaste it from the net.(might have wrong characters.

If u want for example 1280x736 resolution Do:
```
cvt 1280 736
```
and change from the first command of xrandr


Also If U want to do it persistently I used: /etc/gdm/Init/Default  script and add the code just before  > /sbin/initctl -q emit  login-session-start DISPLAY_MANAGER=gdm line.

To do this u must use 
```
sudo gedit /etc/gdm/Init Default 
```

Ask me if u have any questions, just about this methoth cause im not A PRolinux guy :wink:

---

### Post by realzippy on 2011-09-21
Welcome to UF..
...it is Intel GMA 3150 graphics,is it ?
Open terminal,post output from:
```
lspci | grep VGA
```

---

### Post by Miguelbu on 2011-09-21
This is my board: [http://www.asus.com/Motherboards/Intel_CPU_on_Board/AT5NM10I/#overview](http://www.asus.com/Motherboards/Intel_CPU_on_Board/AT5NM10I/#overview)

meanwile im just going to try

---

### Post by Miguelbu on 2011-09-21
Well This happended:

> 00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)


And in Monitors dont have new resolution..

---

### Post by realzippy on 2011-09-21
> **Miguelbu said:**
> [SIZE=2].. tried xrandr and so one.. didn't tried to change xorg.conf because dont know what to do...
[/SIZE]

so post what happened when you tried:

```
xrandr -q
```

```
cat /etc/X11/xorg.conf
```

---

### Post by Miguelbu on 2011-09-21
Xrandr -q (Whats -q for?)
> Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0* 
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  


xorg.conf does not exists, forget to tell that, actually I have in that dir this document: xorg.conf.save wich I cannot change the name and do anything

But in a search i did i have this Document :/usr/share/doc/xserver-xorg-video-nouveau/examples/xorg.conf

And this folder: /usr/share/X11/xorg.conf.d

---

### Post by realzippy on 2011-09-21
So which monitor's screen resolution do you want to change ?
..which resolution do you want?

---

### Post by Miguelbu on 2011-09-21
I Want 1280x1024 in my VGA1 monitor.
I tried: ```
xrandr --newmode VGA1 1280x1024
```

But it doesnt happen anything,

---

### Post by realzippy on 2011-09-21
You have to create that mode ..

```
xrandr --newmode &#8220;1280x1024_60.00&#8243; 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync
```
```
xrandr --addmode VGA1 1280x1024_60.00
```
```
xrandr --output VGA1 --mode 1280x1024_60.00
```

---

### Post by Miguelbu on 2011-09-21
I've Tried this once the problm is that in step two gives me this message:
> xrandr: cannot find mode "1280x1024_60.00"


and when i do Xrandr it actually appears.. 
> VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
  “1280x1024_60.00&#8243; (0xe5)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz


might be about the ("")?

---

### Post by realzippy on 2011-09-21
> **Miguelbu said:**
> 
might be about the ("")?
No,they don't matter.
Can you run
```
rm ~/.config/monitors.xml
```
then log out and back in to "reset" xrandr,
then run the 3 commands again. 
Post commands and output,this makes things more clear than
[I]"and when i do Xrandr"
[/I]
...and please use code tags ;-)

---

### Post by Miguelbu on 2011-09-21
Same Thing:
> mcenter@MCenter-asus:~$ xrandr --newmode “1280x1024_60.00&#8243; 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync
mcenter@MCenter-asus:~$ xrandr --addmode VGA1 1280x1024_60.00
xrandr: cannot find mode "1280x1024_60.00"
mcenter@MCenter-asus:~$ xrandr --output VGA1 --mode 1280x1024_60.00
xrandr: cannot find mode 1280x1024_60.00
mcenter@MCenter-asus:~$ 



---

### Post by realzippy on 2011-09-22
Odd.
No idea.
Will think things over and post when I have found something.
Sorry.

---

### Post by technosysind on 2011-09-22
> Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096

This means that u have current resolutions of 1024 x 768
I'm not sure where the problem is?
Have you tried installing the Experimental drivers??

---

### Post by Miguelbu on 2011-09-22
The problem is that I want to have different resolution like 1280x1024 or 1280x768.

Actually through this methought I can do reslolutions like 1366x768.. but can't do anything with 1280xXXX.

> Have you tried installing the Experimental drivers?? Don't know what u mean with that.

---

### Post by technosysind on 2011-09-22
There are 2 kinds of drivers that you can install
1)Proprietary Drivers 
2)Experimental Drivers

Try Experimental Drivers. I'm using experimental drivers for my Nvidia, I'm sure you will find for your display card also..

---

### Post by realzippy on 2011-09-22
> **technosysind said:**
> There are 2 kinds of drivers that you can install
1)Proprietary Drivers 
2)Experimental Drivers

Try Experimental Drivers. I'm using experimental drivers for my Nvidia, I'm sure you will find for your display card also..

You seem to have missed that OP does not use a nvidia device.

---

### Post by realzippy on 2011-09-22
Which monitor model is VGA-1 ?

---

### Post by Miguelbu on 2011-09-22
My VGA1 output is  a digital square 190M1 19" monitor.

But I can't understend why does this matter. I could try connect the pc to another monitor but i can't see how this is useful.

---

### Post by realzippy on 2011-09-22
Just wanted to know the [panel]("http://www.epinions.com/specs/Nfren_TFT_monitor_19_190M1_16ms")'s native resolution,
which is 1280x1024.
I wondered about that:
*Actually through this methought I can do reslolutions like 1366x768.. but can't do anything with 1280xXXX.*

---

### Post by Miguelbu on 2011-09-22
Yeah I found that really strange too but thats true i just cant do resolutions starter by 1280.

Do u want me to show u how i did?


If I go run:
```
xrandr -addmode VGA1 1366x768
```

Its added ant then I can go to Monitor Preferences and changed to it (Of course is out of ranged)

---

### Post by Miguelbu on 2011-09-22
> Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0* 
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9                      
Atually I can add this resolution only because it appears in LVDS1.. I tried others and couldn't.

What is LVDS1? I found id I change my resolution LVDS1 also changes to the new one:
> Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
LVDS1 connected **800x600**+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0* 
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected **800x600**+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9                      




ALso in Xorg.conf that is in my /usr dir it says I have "nouveau" Driver. That one is compatible with Intel?

---

### Post by Miguelbu on 2011-09-23
[SOLVED]
Solution:

My main problem was that the code mode dind't have the same name

SO:

1ºCommand
```
xrandr --newmode "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```
2ºCommand
```
xrandr --addmode VGA1 1280x1024
```

"1280x1024" is the name You want to give him (U can actually call it what ever u want)

AND NOT:

```
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```
2ºCommand
```
xrandr --addmode VGA1 1280x1024
```

If U Want to Use in command 1º the name of the mode "1280x1024_60.00" in command 2º it must have the same name.

Also Instead of copypaste the code from forum I did:

```
cvt 1280 1024
```

Use This code To generate part of 1º Command instead of copypaste it from the net.(might have wrong characters.

If u want for example 1280x736 resolution Do:
```
cvt 1280 736
```
and change from the first command of xrandr


Also If U want to do it persistently I used: /etc/gdm/Init/Default script and add the code just before  > /sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm line.

To do this u must use 
```
sudo gedit /etc/gdm/Init Default 
```

Ask me if u have any questions, just about this methoth cause im not A PRolinux guy ;)

---

### Post by realzippy on 2011-09-23
Hm,I do not know why you had those problems.
For sure the problem is not the "_60" term as you described.
For example,here on my machine this works without trouble:
```
me@mine:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   [COLOR="SeaGreen"]1366x768       60.0*+[/COLOR]
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)

me@mine:~$ cvt 1280 768
# 1280x768 59.87 Hz (CVT) hsync: 47.78 kHz; pclk: 79.50 MHz
Modeline "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync

me@mine:~$ xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync

me@mine:~$ xrandr --addmode LVDS1 "1280x768_60.00"
me@mine:~$ xrandr --output LVDS1 --mode "1280x768_60.00"
me@mine:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 768, maximum 8192 x 8192
LVDS1 connected 1280x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
   [COLOR="SeaGreen"]1280x768_60.00   59.9* [/COLOR]
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by Miguelbu on 2011-09-23
Yes I know but the 60.00 made the difference or just one character was different don't know I advise people to use the cvt method.

Now I'm going to explore more of ubuntu and build my HTPC.):P

---

