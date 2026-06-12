---
title: "Help needed for my screen setting please"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by kudos1uk on 2007-08-20
I'm really stuck, please can I beg some help, I have spent the weekend trying to sort this out and reading up without any luck. I'm a total Newbie.

I have a Sony Vaio Picturebook PCG-C1VN (aka C1VE)  but can't make it use the 1024x480 widescreen.

The laptop has a  "ATI Technologies Inc 3D Rage P/M Mobility" chipset.

At the moment its set to use Vesa (thanks to gn2 who helped me get a working screen), when I installed using xubunu 6.06.1 I initially set it to ATI but did not work.

From what I have read I need to edit xorg.conf entries from 1024x768 1024x480. (but not sure that will work with vesa?) although its not currently 1024?


I have [read up]("http://ubuntuforums.org/showthread.php?t=498932") and everyware says type this:

> gksudo gedit /etc/X11/xorg.conf

Into terminal but when I do that it asks for my password then HDD activity and back to prompt, nothing opens?

I'm really lost.

---

### Post by njknight on 2007-08-20
Have you tried the ENVY script?  see [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
this is states it is for ATI and Nvidia graphics systems.

---

### Post by kudos1uk on 2007-08-20
Thanks.

 I just installed it but where my screen is the wrong size I can see or get to anything under where it says "install the ATI driver" the rest is off the desktop.

[IMG]http://albertomilone.com/images/gui1small.gif[/IMG]

---

### Post by kudos1uk on 2007-08-20
I also just tried Envy's textual interface which I could use but said my card is not supported.

---

### Post by kudos1uk on 2007-08-20
I might have found something to help if someone would be kind enough to take a look and translate into something I can make sense of.

> Post-Install -- getting X working
Ubuntu does not deal correctly with the Vaio display out of the box. The first thing you need to do is to modify the grub menuconfig and remove the "splash" option from the default kernel startup line. This option seems to completely hose the vaio display.

Next, because the default Ubuntu install fails to correctly detect the Vaio display driver, you'll need to create a new /etc/X11/xorg.conf file. run "Xorg --configure". This should create the file "xorg.conf.new" in your root directory. Note that the mouse will be detected incorrectly, so you'll need to edit this file, changing the reference to "/dev/mouse" to "/dev/psaux". 

To test the new X config, run "Xorg -config ./xorg.conf.new". This should bring up an empty X desktop sized correctly. Exit by pressing Ctrl-Alt-backspace. Copy xorg.conf.new to /etc/X11/xorg.conf. 


[http://www.swampgas.com/linux/vaio.html](http://www.swampgas.com/linux/vaio.html)

---

### Post by kudos1uk on 2007-08-20
I also read here [http://www-jcsu.jesus.cam.ac.uk/~mma29/c1/#graphics](http://www-jcsu.jesus.cam.ac.uk/~mma29/c1/#graphics) I need a modeline but dont know how to do that?

ModeLine "1024x480" 65.00 1024 1032 1176 1344 480 488 494 563 -hsync -vsync

also slightly different model here [http://ubuntuforums.org/showthread.php?t=156896&highlight=sony+picturebook+resolution](http://ubuntuforums.org/showthread.php?t=156896&highlight=sony+picturebook+resolution) but same modeline even thogh a different chipset:

ModeLine "1024x480" 65.00 1024 1032 1176 1344 480 488 494 563 -hsync -vsync

---

### Post by ranf on 2007-08-22
You need to edit the file "/etc/X11/xorg.conf". 
```
sudo nano /etc/X11/xorg.conf
```

There is a section labelled Monitor. That's where the Modeline line belongs to.

---

