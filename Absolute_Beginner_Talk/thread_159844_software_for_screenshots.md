---
title: "software for screenshots"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-04-13
Does anyone know of a software that will allow the user to take a selected section of a screenshot and not just the whole screen. Preferably free!:)

---

### Post by rfruth on 2006-04-13
Alt-Prnt Screen will capture just the highlighted area [https://wiki.ubuntu.com/TakingScreenshots?highlight=%28screenshot%29]("https://wiki.ubuntu.com/TakingScreenshots?highlight=%28screenshot%29")

---

### Post by joselin on 2006-04-13
Gimp allow you to capture only a window.

Regards.

---

### Post by Sbarton on 2006-04-14
[QUOTE=rfruth]Alt-Prnt Screen will capture just the highlighted area [https://wiki.ubuntu.com/TakingScreenshots?highlight=%28screenshot%29]("https://wiki.ubuntu.com/TakingScreenshots?highlight=%28screenshot%29")[/QUOTE]

Thanks for reply, but when I try that I still get the whole screen which shows the highlighted section and not just the highlighted section,which is what I am after.
Regards

---

### Post by joshrobinson on 2006-04-14
[QUOTE=Sbarton]Thanks for reply, but when I try that I still get the whole screen which shows the highlighted section and not just the highlighted section,which is what I am after.
Regards[/QUOTE]


as someone said above, you can use GIMP to get screenshots.. it should be in applications then graphics.. open it up or install it if you have to

click file > aquire > screenshot

you can do just a highlighted window, full screen, and you can give it a wait time.. so if you want to make it wait 10 seconds you can minimize gimp or other programs to make sure it captures everything how you want it

---

### Post by gingermark on 2006-04-14
If you don't mind a KDE app, then KSnapshot works great.

---

### Post by Sbarton on 2006-04-14
[QUOTE=gingermark]If you don't mind a KDE app, then KSnapshot works great.[/QUOTE]

I have used Ksnapshot before in my Mepis setup.And your right this does what I want, I was hoping though that ubuntu/gnome would have similar. If necessary I will make an attempt to install KSnapshot into Ubuntu.
Thanks and regards.

---

### Post by taurus on 2006-04-14
Why install extra stuff when Gimp can do the job perfectly fine!!!  Tell it whether you want the whole screen or just a window and the delay time...

---

### Post by hw-tph on 2006-04-14
If you have ImageMagick installed (which is quite common since it is a dependancy for a lot of applications), you can use import. Try **import myscreenie.png** - this will make the cursor a crosshair. Select the window you want to capture and a neat .png file called myscreenie.png will be found in your current directory. import is smart, so if you use another file extension it will create the proper type of file (like .jpg).


Håkan

---

### Post by Sbarton on 2006-04-14
[QUOTE=hw-tph]If you have ImageMagick installed (which is quite common since it is a dependancy for a lot of applications), you can use import. Try **import myscreenie.png** - this will make the cursor a crosshair. Select the window you want to capture and a neat .png file called myscreenie.png will be found in your current directory. import is smart, so if you use another file extension it will create the proper type of file (like .jpg).


Håkan[/QUOTE]

Thanks. I have installed Imagemagick via Synaptic. I do not see this program under Gnome menu. Is this right or am I missing something?
regards

---

### Post by PhilOSparta on 2006-04-14
imagemagick is a group of command line tools.  It doesn't appear on the menu.
Check out this page for all the command line options and their capabilities.

[http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)

---

### Post by taurus on 2006-04-14
[QUOTE=Sbarton]Thanks. I have installed Imagemagick via Synaptic. I do not see this program under Gnome menu. Is this right or am I missing something?
regards[/QUOTE]
Run it from a terminal, Applications -> Accessories -> Terminal.

---

### Post by Sbarton on 2006-04-14
Thanks to all of you for your input. I must be honest and say I am trying to keep command lines to as little as I can. I have tried Gimp and although it does what I want, it is easier (for me) to use something like KSnapshot. In windows I use MWsnap and that is simple yet offers options. Anyone know if I could install KSnapshot into Ubuntu, and how?
Thanks and regards.:)

---

### Post by joshrobinson on 2006-04-14
[QUOTE=Sbarton]Thanks to all of you for your input. I must be honest and say I am trying to keep command lines to as little as I can. I have tried Gimp and although it does what I want, it is easier (for me) to use something like KSnapshot. In windows I use MWsnap and that is simple yet offers options. Anyone know if I could install KSnapshot into Ubuntu, and how?
Thanks and regards.:)[/QUOTE]


im using dapper drake (6.06) of ubuntu.. but it should be in the same place

click applications then add/remove

knapshot should be under graphics, put a check next to it. then click ok to install

then it will be in applications graphics :-D

---

### Post by stalefries on 2006-04-14
One thing that all these people mentioning the Gimp forgot is that you can crop your screenshot in the Gimp. Just select the Crop tool, and drag out the box area you want your screenshot to encompass.

---

### Post by Sbarton on 2006-04-15
[QUOTE=joshrobinson]im using dapper drake (6.06) of ubuntu.. but it should be in the same place

click applications then add/remove

knapshot should be under graphics, put a check next to it. then click ok to install

then it will be in applications graphics :-D[/QUOTE]

Thanks! I forgot all about ADD/Remove Applications menu. It is now installed!:) 
**Stalefries: ** I had already used Gimp the way you suggested, it works fine but is slower than KSnap. Thanks for your input though!
Regards:)

---

### Post by hw-tph on 2006-04-15
This is right. There is no graphical for ImageMagick but it provides a set of command line programs - like import - and libraries that can be used by other programs.


Håkan

---

### Post by crazy ivan on 2008-07-19
Gimp just takes a while to load. So as I look at it now, **ksnapshot** is the only packaged tool which has this functionality. 
Just installed the KDE4 version (attention! not in binary path - check out /usr/lib/kde4/bin), and am fully satisfied. Nice shortcuts and a very good looking "region" function.
For Gnome purists I found [Desktop Data Manager]("http://data-manager.sourceforge.net/"), but its kinda buggy. Especially the red stripes at the sides of a shot annoy me.
Still I would prefer "Printscreen" to simply have this functionality aswell.

---

