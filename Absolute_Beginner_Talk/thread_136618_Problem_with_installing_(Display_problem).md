---
title: "Problem with installing (Display problem)"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by darthvivi on 2006-02-26
First off, let me say I'm a complete newb and don't really know much about what I'm talking about.

Last night I installed Xubuntu, since I want to use Linux but I'm using and old computer. (64MB of RAM) It took a long time to install, but I'm 99% sure I followed all the the install instructions correctly.

First I tried to start the GUI by typing "startxfce4". When I typed that, a weird  bar composed of red and green vertical lines appeard at the top of the screen, about an inch thick going all the way across the screen horizontally. 

I thought maybe installing GDM might help, and it said to do that in the Xubuntu guide, so I did. When I finished doing that, I ran GDM, but the same thing happened, only this time there was a drum sound. I noticed when I moved my mouse, a couple of tiny black lines appeared over the bigger bar.

I tried following the "Changing Resolution/Refresh Rate in Xorg HOWTO" but I didn't really know what I was doing. The bar changed from vertical lines to and orange gradient. And now for some reason GDE fails to start.

I'm so confused...

---

### Post by darthvivi on 2006-02-26
I did a little bit more experimenting and noticed first of all that the rectangle bar thing at the top of the screen changes size and color when I reconfigure the resolution/color. Also I tried "username" [TAB] "password" and it apparently logged me in, because the rectangle changed to light blue and then some other color. I can see something happening when I move the mouse, and something happening when I right click.

---

### Post by patrick295767 on 2006-02-26
[QUOTE=darthvivi]First off, let me say I'm a complete newb and don't really know much about what I'm talking about.

Last night I installed Xubuntu, since I want to use Linux but I'm using and old computer. (64MB of RAM) It took a long time to install, but I'm 99% sure I followed all the the install instructions correctly.

First I tried to start the GUI by typing "startxfce4". When I typed that, a weird  bar composed of red and green vertical lines appeard at the top of the screen, about an inch thick going all the way across the screen horizontally. 

I thought maybe installing GDM might help, and it said to do that in the Xubuntu guide, so I did. When I finished doing that, I ran GDM, but the same thing happened, only this time there was a drum sound. I noticed when I moved my mouse, a couple of tiny black lines appeared over the bigger bar.

I tried following the "Changing Resolution/Refresh Rate in Xorg HOWTO" but I didn't really know what I was doing. The bar changed from vertical lines to and orange gradient. And now for some reason GDE fails to start.

I'm so confused...[/QUOTE]
   
try first to make sure the resolution is okay:
```
dpkg-reconfigure xserver-xorg
```
  
as u said, first, try gdm: 
```
apt-get -f install gdm
/etc/init.d/gdm start
```
  
then, check the session that xfce ...
  
Otherwise, try fvwm:```

apt-get -f install fvwm
apt-get -f install fluxbox
```
  U can try them to work with first to try frorm selecting them in the gdm screen (i wanna use this)
the gdm will setup ur config automatically and store info for instance in 
.xsession
that should ocntain fvwm if u 'd like fvwm 
  
Also, if your gdm running, and wanna startx from the console:
do :
startx -- :2
then u'll start session X on the display 2
  
May the Force Be with You :-)

Greetz

---

### Post by darthvivi on 2006-02-26
I've already tried like 6 different resolutions and none of them worked.

Also it won't let me install whatever it is you were talking about.

---

### Post by darthvivi on 2006-02-26
Alright I tried reinstalling everything using the Xubuntu guide. I'm 100% sure I did everything correctly, however while following the screenshots I accidentally followed an optional step I really didn't need:

[http://shots.osdir.com/slideshows/slideshow.php?release=517&slide=23](http://shots.osdir.com/slideshows/slideshow.php?release=517&slide=23)

What that does is make a fancy login page for Gnome. I did that the first time I installed Xubuntu as well, I didn't realize it was optional.

So I went on to the next step:

[http://shots.osdir.com/slideshows/slideshow.php?release=517&slide=24](http://shots.osdir.com/slideshows/slideshow.php?release=517&slide=24)

typed "gdm" and then "sudo gdm". 

Now I'm right back where I was before. Drum noise, with a weird colored bar at the top of the screen.

Argh...this is pretty frustrating.

---

