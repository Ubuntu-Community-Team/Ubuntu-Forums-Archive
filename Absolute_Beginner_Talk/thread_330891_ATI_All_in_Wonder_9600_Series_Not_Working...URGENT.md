---
title: "ATI All in Wonder 9600 Series Not Working...URGENT!!"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Fingerz91 on 2007-01-03
Hello All!

While I am new to ubuntu I am not new to Linux. My computers at work run Linspire and Freespire, but I wanted to make a jump from them to ubuntu..... 

When I installed ubuntu my screen resolution was set to a horrible 800x600 when I really want a 1024x768 like on my Linspire systems..... 

I now have one machine at work that I keep attempting to install ubuntu on, and it is not working with this horrible resolution. I also cannot use firefox to play embedded video such as flash, windows media, ect. out of the box like in Linspire.....

I could really use some help, or I might need to go back to Linspire

---

### Post by BarfBag on 2007-01-03
Welcome to Ubuntu!

Do you have the ATI graphics driver installed?  It should solve your problem.  [Here's instructions on how to install it.]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")  Then, just go to System -> Preferences -> Screen Resolution and change it.

Unlike Linspire, Ubuntu is free.  Not as many things work out of the box (certain types of multimedia, etc).  In my opinion, the best way to get things working fast is through [Automatix]("http://www.getautomatix.com/").

If you need any more help, don't hesitate to ask.  :)

---

### Post by Fingerz91 on 2007-01-03
PERFECT!!!!

Someone should sticky this!

it worked without an issue!!!

ubuntu is great so far.... i'll see how my employees like it over Linspire....

All i need is a multimedia player for Firefox 2.0 to play windows media, flash, ect

---

### Post by BarfBag on 2007-01-04
> **Fingerz91 said:**
> PERFECT!!!!

Someone should sticky this!

it worked without an issue!!!

ubuntu is great so far.... i'll see how my employees like it over Linspire....

All i need is a multimedia player for Firefox 2.0 to play windows media, flash, ect

Sorry for my slow reply.  I had to do a search to find this topic again.

In my opinion, the best multimedia player for Firefox is MPlayer.  It's a little tricky to install, but if you use Automatix, it'll setup with no hassle at all.  To get Flash, you also have to install the Adobe Flash player (which is also in Automatix).

I'll PM you in case you think this topic is dead.

---

### Post by mykalreborn on 2007-01-04
>  out of the box like in Linspire.....

yeah, but isn't life more interesting this way? :D

---

### Post by NT4usB on 2007-01-04
> **Fingerz91 said:**
> PERFECT!!!!

Someone should sticky this!

it worked without an issue!!!...

Did you get flgrx to work with it or did you settle for the mesa?
I have a 9600pro that refused to work with this or any other method except:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
what does $fglrxinfo show, this:
```
ct@wimp:/etc/X11$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6234 (8.32.5)
```
or this:```
ct@wimp:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```

---

