---
title: "linux install help laptop"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by w00taliter on 2007-05-26
Hello i want to install ubuntu on my laptop but for some reason before it hits the live disk i do not know what to do. my laptop is a Toshiba Satellite M65-S821


its video specs are

    * Graphics Processor / Vendor
    * Intel GMA 900

    * Video Memory
    * Dynamic Video Memory Technology 3.0

for more specs here are the lists [http://reviews.cnet.com/laptops/toshiba-satellite-m65-s821/4507-3121_7-31660110.html?tag=sub](http://reviews.cnet.com/laptops/toshiba-satellite-m65-s821/4507-3121_7-31660110.html?tag=sub)

If any one has any ideas as to how to get this installing properly with working drivers ect please help

---

### Post by oilchangeguy on 2007-05-26
quote "but for some reason before it hits the live disk"
can you be a little more clearer????????? what is it doing?

---

### Post by H.E. Pennypacker on 2007-05-26
I have to ask the same question as oilchangeguy.  The more time we spend trying to figure out what your post says, the less time we have to actually provide support.

---

### Post by w00taliter on 2007-05-26
sorry you know while doing an install it hits the desktop from the live disk ? well before it hits the live disk desktop it just crashes.

---

### Post by w00taliter on 2007-05-26
help please i hope my second post explained it more

---

### Post by oilchangeguy on 2007-05-26
> **w00taliter said:**
> sorry you know while doing an install it hits the desktop from the live disk ? well before it hits the live disk desktop it just crashes.

this makes no sense. a problem occurs when it gets to the desktop, no wait, it happens before it gets to the desktop. make up your mind. when does the problem occur? what is happening when the problem occurs?

---

### Post by w00taliter on 2007-05-26
before it gets to the desktop

---

### Post by w00taliter on 2007-05-26
here is the error message i get from it
I810(0): NO VIDEO BIOS MODE FOUND
SCREENS FOUND BUT NONE HAVE A USABLE CONFIGUREATION

FATAL ERROR:
SCREENS FOUND

---

### Post by Cows on 2007-05-26
Never seen this problem before but I think the xorg doesn't have a correct configuration for you.. this is just my hypothesis.

---

### Post by meng on 2007-05-26
Okay I think I understand what the poster is seeing, but I can't be sure of the solution. Can you try running in safe graphics mode? Otherwise try installing from the Alternate CD instead of the Desktop CD.

---

### Post by w00taliter on 2007-05-26
if i run it and install it under safe mode will i be able to run it without safe mode once its done installing?

---

### Post by Pizzarth on 2007-05-26
yes, but I had the same problem, and it was caused by the xorg.conf file. 

do:

```

sudo nano /etc/X11/xorg.conf
find something like this:
> Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

```

if the driver says "vesa" try changing it to i810, then type
```
startx
``` to get the x server up again.

---

### Post by meng on 2007-05-26
Probably.

---

### Post by w00taliter on 2007-05-26
> **Pizzarth said:**
> yes, but I had the same problem, and it was caused by the xorg.conf file. 

do:

```

sudo nano /etc/X11/xorg.conf
find something like this:


```

if the driver says "vesa" try changing it to i810, then type
```
startx
``` to get the x server up again.

 how do i change it to i810? i just want to get as much info as i can before i try installing it

---

### Post by Pizzarth on 2007-05-26
how do you change it? exactly as it seems. nano's just a text editor program. when you open that up, you'll see the file with all the writing in there. Arrow key down to where it has something similar to what I posted up there with the video card, it's not hard to miss. the driver will probably say vesa, using the arrow keys move it over to there, and delete vesa, and type up i810, just like in any other text editor. oh wait, nano sometimes has a different deleting thing, try using pico or whichever text editor you know about.

---

### Post by w00taliter on 2007-05-26
> **Pizzarth said:**
> how do you change it? exactly as it seems. nano's just a text editor program. when you open that up, you'll see the file with all the writing in there. Arrow key down to where it has something similar to what I posted up there with the video card, it's not hard to miss. the driver will probably say vesa, using the arrow keys move it over to there, and delete vesa, and type up i810, just like in any other text editor. oh wait, nano sometimes has a different deleting thing, try using pico or whichever text editor you know about.

when i did the steps nothing appeard but the text editor showed up

---

### Post by w00taliter on 2007-05-26
help please i want to do the alternate disk for the last option

---

### Post by Pizzarth on 2007-05-26
were you in root at the time?

---

### Post by w00taliter on 2007-05-26
i was installing it so i thought i was automaticaly in root

---

### Post by jerrylamos on 2007-05-26
I've seen that one.  
#1.  Can you get into your BIOS setup and check to see if there is a shared video memory setup?  On mine there was, then set it to the highest memory it can do.  Default might be 1024K, and you might be able to bump it up to 4096K or 8192K or more.
#2.  Try booting again.  If it still fails, then try booting in safe graphics mode.
#3.  If it is still failing to start full screen mode, then see if you are at a "command line".
       If you aren't, push Ctrl-Alt-F1 to try to get a command line you can enter keystrokes on.
#4.  Enter the following command:
sudo dpkg-reconfigure -phigh xserver-xorg
Note!  there are no blanks in dpkg-reconfigure and in xserver-xorg
This should get you into a set of menus to set your video driver and screen resolution.
A safe but slow driver is VESA, the same one the safe graphics mode uses.  Then choose a screen resolution that you know your monitor will support, example 1024x768 color depth 16.
#5.  If the dpkg.... seems to complete, then do:
startx
to get the desktop going.
In general it helps us when you have a problem to post what the screen has just displayed.
Cheers, Jerry

---

### Post by H.E. Pennypacker on 2007-05-26
You have to do what Pizzarth is telling you to do.  I would normally not recommend Nano, but it's obvious you do not have a graphical user interface.

Go back to the command line (terminal) as you have done before.  This time, type sudo nano /etc/X11/xorg.conf.  This will allow you to edit the file (xorg.conf).  Xorg.conf is broken down into sections.  Go to the Section "Device."  Under device, you will see "driver."  Next to driver, you probably currently see "vesa."  Change vesa to "i810".  That is a letter i (notice the i, not 1), and the 810.  Once you have done this, save the file and close out of Nano.  Close out of Nano by pressing CTRL-X.  You will be asked if you want to save the changes.  Say yes.  Once you have closed Nano, you'll be taken back to the command line.  Enter "startx" (without the quotes).

If you do not know how to use Nano, please see:

[http://www.tqnyc.org/tutorial/nano/](http://www.tqnyc.org/tutorial/nano/)

---

### Post by w00taliter on 2007-05-26
> **H.E. Pennypacker said:**
> You have to do what Pizzarth is telling you to do.  I would normally not recommend Nano, but it's obvious you do not have a graphical user interface.

Go back to the command line (terminal) as you have done before.  This time, type sudo nano /etc/X11/xorg.conf.  This will allow you to edit the file (xorg.conf).  Xorg.conf is broken down into sections.  Go to the Section "Device."  Under device, you will see "driver."  Next to driver, you probably currently see "vesa."  Change vesa to "i810".  That is a letter i (notice the i, not 1), and the 810.  Once you have done this, save the file and close out of Nano.  Close out of Nano by pressing CTRL-X.  You will be asked if you want to save the changes.  Say yes.  Once you have closed Nano, you'll be taken back to the command line.  Enter "startx" (without the quotes).

If you do not know how to use Nano, please see:

[http://www.tqnyc.org/tutorial/nano/](http://www.tqnyc.org/tutorial/nano/)

i did just that but it still does not work >_<   it is driveing me crazy i also  tried the advice by jerry and still no luck i checkt the integraty of cd and it said everything was fine but im still getting this error

---

### Post by w00taliter on 2007-05-26
do you think its my laptop im using another distro but i dont like it so i was hopeing to switch to ubuntu

---

### Post by w00taliter on 2007-05-26
bump

---

### Post by H.E. Pennypacker on 2007-05-26
> **w00taliter said:**
> do you think its my laptop im using another distro but i dont like it so i was hopeing to switch to ubuntu

We know the problem is with your laptop (a hardware issue), but despite it being the problem, you can still work around it.

I too have an Intel graphics card, and I am not having any problems.  

Are you trying to install Feisty?  If not, make sure it is Feisty.  To rule out any problems with your CD, try it on another computer, or simply burn another CD.

---

### Post by w00taliter on 2007-05-27
yea it works i have used this on another computer

---

### Post by w00taliter on 2007-05-29
bump also this is the cd i have received from shipit(i think thats it the one off of the main page) but i really want to have this running. should i just give up

---

### Post by Loopsurgeon on 2007-11-29
Hey I found thisd old string cuz I am having the same problem essentially. Linux will not install. I have several flavors, those that will run from LiveCD do not find the wireless card; others including Ubuntu 7.04 just don't work at all. It seems mainly to be a bunch of drivers including the video. This is an HP Pavilion dv9010us. It rocks and is only a year old but no good Linux drivers. Is there some problem writing drivers for HP laptops or what. There seem to be alot of unanswered posts about HP laptop woes. Any help possible with the Fedora 8 or the new Ubuntu?

---

