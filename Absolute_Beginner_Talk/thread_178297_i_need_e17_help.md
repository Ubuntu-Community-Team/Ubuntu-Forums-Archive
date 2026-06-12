---
title: "i need e17 help"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-05-17
i installed it following this howto - [https://wiki.ubuntu.com/InstallingE17Howto](https://wiki.ubuntu.com/InstallingE17Howto) 
i tried entering */usr/local/bin/enlightenment* and then doing *istartx* and got a no such thing error (and there is no such) thing. the only e17 is in /opt and there doesn't appear to be anything in there that would get it to start. so, what do i need to do to start e17 from startx? thanks.

---

### Post by patrick295767 on 2006-05-17
You can try my automatic script : 
  
Let me know if it worked EFFORTLESS &if you liked it  !!
(for breezy linux :-D )
```
 #!/bin/bash
date
##################### .fvwm2rc = part II = e17 & engage ################"
##apt-get -f -y install e17 should be installaed at the end
## fbsetroot should be installed too
mkdir /root/miniram
echo "Installing e17 !! enlightenment "
apt-get -f -y install enlightenment
apt-get -f -y install gtk-theme-switch gtkgl-dev gtkter

apt-get -f -y install libtool
apt-get -f -y install libxxf86vm-dev
apt-get -f -y install libxxf86vm-dev

apt-get -f -y install flex
apt-get -f -y install xlibmesa-dev
apt-get -f -y install xlibmesa-gl-dev
apt-get -f -y install libglu1-xorg-dev

cd /root/miniram
rm /root/miniram/dr17-2.sh
wget http://patrick295767.sitesled.com/miniram/dr17-2.sh
## I'll install some packages, download the easy_e17.sh, and install it ! :-)
chmod +x dr17-2.sh
./dr17-2.sh

date
##########################################################################

```
  
Greetings from Patrick,
==  
Btw, you had nice kde desktop, you can try my desktop too if you like fvwm !
  
===
if it's fully installed, normally, you can start it with gdm 
apt-get -f -y install gdm
  
that'll configure everythg for you :-) !

---

### Post by fuscia on 2006-05-18
patrick, thanks for your response. i don't understand all that script and how fvwm fits in. also, i don't want to use gdm. i find it simpler to just edit .xinitrc whenever i want to switch wms.

it looks like i didn't have e17 installed correctly. i don't understand cvs either. the more i read about it, the more baffled i become.

---

### Post by skinnygmg on 2006-05-18
this will answere your cvs q's...

[http://www.nongnu.org/cvs/](http://www.nongnu.org/cvs/)

---

### Post by gashcrumb on 2006-05-18
[QUOTE=fuscia]patrick, thanks for your response. i don't understand all that script and how fvwm fits in. also, i don't want to use gdm. i find it simpler to just edit .xinitrc whenever i want to switch wms.

it looks like i didn't have e17 installed correctly. i don't understand cvs either. the more i read about it, the more baffled i become.[/QUOTE]
That script installes e17 into /opt.  So the path to the "enlightenment" binary is in /opt/e17/bin/enlightenment.  You may also want to add /opt/e17/bin to your PATH either in your .bashrc or .profile so you can try out some of the included goodies.

BTW, it's far from finished, I've been using it on my work laptop for a few days now and it's nice, but there's definitely some missing functionality here and there that you'll come across.

---

### Post by fuscia on 2006-05-18
[QUOTE=gashcrumb]BTW, it's far from finished, I've been using it on my work laptop for a few days now and it's nice, but there's definitely some missing functionality here and there that you'll come across.[/QUOTE]

it's sounding more and more like i should avoid it until something more for the masses comes out.

---

### Post by pormogo on 2006-05-18
not to try and thread hyjack but I've noticed that everytime I try to task switch (alt+tab) style E17 faults and needs to restart? Does anyone know why that might be?

---

### Post by Sef on 2006-05-19
Pormogo:

> not to try and thread hyjack but I've noticed that everytime I try to task switch (alt+tab) style E17 faults and needs to restart? Does anyone know why that might be?

Please start a new thread for your question.  If you want to make a link to here from your thread, please do so, but don't you-know-what.

---

### Post by wrtrdood on 2006-05-19
I've found the best way to build E17 is by using Rasterman's script.  There's a nice new GUI that works quite well too.  You can find it at: [http://sevcsik.atw.hu/?page=e17-updater]("http://sevcsik.atw.hu/?page=e17-updater")

I wouldn't say that there's necessarily any missing functionality.  Everything I need to do I can do easily.  It's true that due to the developmental nature of  E17 you must be prepared to take extra steps to get some things done but it's not difficult by any means.  I choose to use the Run dialog to kick off most of what I need.  I've used both KDE and Gnome apps with no problems.  they work as expected.  If you mean that changing themes and other things are more troublesome, yes.  But I happen to like the default theme a lot so it's not an issue for me.

E is cleaner, faster, and much nicer to look at than anything else I've used.  I've been running it for close to a year now and have only rarely had problems.

One thing to note:  because of real problems with sourceforge, the team set up their own anonymous CVS server and new builds have been much smoother ever since.  For those interested, you'll find it at

 > :pserver:anonymous@anoncvs.enlightenment.org:/var/cvs/e

I've tried a few of the other methods and find that CVS is the most reliable and easiest approach for anyone interested in trying out E.

Have fun!

---

### Post by mattman on 2006-05-21
When i try installing E17 with the updater or the script I get this error.

automake: src/modules/engines/software_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_xcb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/fb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/buffer/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_qtopia/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/directfb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/gl_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/cairo_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/xrender_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/xrender_xcb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
Configuration of evas failed. Do you want to continue? [yes]

If anyone could help with this I would appreciate it.

---

### Post by ThomasAdam on 2006-05-21
[QUOTE=patrick295767]You can try my automatic script : 
  
Let me know if it worked EFFORTLESS &if you liked it  !!
(for breezy linux :-D )
```
 #!/bin/bash
date
##################### .fvwm2rc = part II = e17 & engage ################"
##apt-get -f -y install e17 should be installaed at the end
## fbsetroot should be installed too
mkdir /root/miniram
echo "Installing e17 !! enlightenment "
apt-get -f -y install enlightenment

```[/quote]

Actually expressing all of the packages you want to use on one single line is much "better" as it means you don't have to spawn multiple commands.  This then obliterates the need for these so-called "wrapper" scripts.

-- Thomas Adam

---

### Post by aktiwers on 2006-05-21
Fuscia is it because you dont know how to run the script?
I have used some of Patricks scripts, and it is pretty much like Automatix.

Just copy and paste the script into a text editor and save it in /root/ as script.sh.

Then just copy paste this into terminal.

```

chmod +x  /root/script.sh 
cd /root
./script.sh 
```

Edit:

Maybe you need a sudo on the last line

sudo ./script.sh

I had to do that for some reason?

---

### Post by fuscia on 2006-05-21
[QUOTE=aktiwers]Fuscia is it because you dont know how to run the script?
I have used some of Patricks scripts, and it is pretty much like Automatix.

Just copy and paste the script into a text editor and save it in /root/ as script.sh.

Then just copy paste this into terminal.

```

chmod +x  /root/script.sh 
cd /root
./script.sh 
```

Edit:

Maybe you need a sudo on the last line

sudo ./script.sh

I had to do that for some reason?[/QUOTE]

i don't know how to run it, but i'm also wondering what fvwm has to do with it, if anything. (do i sound crazy?)

---

### Post by aktiwers on 2006-05-21
[quote=fuscia]i don't know how to run it, but i'm also wondering what fvwm has to do with it, if anything. (do i sound crazy?)[/quote] 

I don't know either.. actually I dont even know what it is, I only know how to run the script :mrgreen:

But look at the title of the script, maybe that helps? :confused:


> ##################### .fvwm2rc = part II = e17 & engage ################"

---

### Post by Sef on 2006-05-22
> (do i sound crazy?)

No you don't sound crazy.

---

### Post by fuscia on 2006-05-22
[QUOTE=aktiwers]I don't know either.. actually I dont even know what it is, I only know how to run the script :mrgreen:

But look at the title of the script, maybe that helps? :confused:[/QUOTE]

fvwm is a window manager which i've never been terribly fond of. that's why i want to make sure about it.

[quote=Sef]No you don't sound crazy.[/quote]

cool!

---

### Post by fuscia on 2006-05-22
so, i tried using e17 updater and got that same error *automake: src/modules/engines/software_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally* (while configuring evas) that mattman got.

i'm still having trouble understanding what to do with patrick's script. i know longer care about fvwm. i just want this to work somehow.

---

