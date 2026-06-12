---
title: "Trouble (I think) with ATI Graphics CARD"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by eUsha on 2007-11-20
Hi all, :)

I'm new to Linux. In fact tonight is my first night with Ubuntu Linux. And this is my problem.

After installing Ubuntu (64 bit)  I received a message (a bubble) stating that in order to fully utilize the hardware
[ referring to my ATI Graphics card]  an update of driver was necessary. So I followed the prompts and Ubuntu did the whole updating. Then it asked me that a restart was necessary for the change. So I did.

Then came the unexpected. After the booting screen, my screen goes blank (dark). The Monitor is still awake ( or else monitor will say that it is going to sleep), but it's just black. Can anyone Help me with my problem. Here is a little info about my System:

Processor: AMD  Athlon 64 X2 Dual
Graphics: ATI Radeon HD2900 XT

If you think you need more information please let me know.

OHHH, If it helps, I'm dual booting with Windows XP Professional 32 bit.

Any Help will be greatly appreciated.

---

### Post by Vadi on 2007-11-20
Is your system 64 or 32bit?

As for the card itself - looks like something went wrong with the driver. I don't have that card unfortunately, so I won't be able to help you much there :(

---

### Post by eUsha on 2007-11-21
My AMD is a 64 bit processor and my Ubuntu 7.10 is also 64 bit.

---

### Post by Vadi on 2007-11-21
I believe you're in luck, this article ([click]("http://www.phoronix.com/scan.php?page=article&item=921&num=1")) was just written yesterday.

---

### Post by eUsha on 2007-11-21
Thanks alot.:)

So The problem really is the driver. Now the next step is how do I uninstall the (ATI)  Driver that I upgraded to. Is there a way I can fix this problem using the Ubuntu CD or some how reverting that change, Because at this point I can't load Ubuntu because right after the loading screen my screen goes blank.

---

### Post by Jense on 2007-11-21
When the Xserver hangs on startup push
Ctrl + Alt F2
this will open a terminal. Login and enter

sudo nano /etc/X11/xorg.conf

nano is a simple texteditor, it should be installed, but I am not sure - you might need to install it first

sudo apt-get install nano

the file xorg.conf is a configuration file for the xserver. Go to section device, the identifier should say something with ati. Change the driver to

"ati"

This should load the default ati driver and will enable you to start the xserver

You woun't have full 3d support, so things like compiz will not work, but you can use your linux system. To fix the proper driver you will have to look at the article or need sombedy else to help you

Hopes this helps

---

### Post by Jense on 2007-11-21
I foregot, you can check out weather the xserver is working if you start it from the console (ALT CTrl F2,3,4,5,etc)

startx

this will drop you back on the console if there is a problem (at least in some cases) and it will print out an errormsg. I am not sure if you need to reboot to check out the driver.

---

### Post by Vadi on 2007-11-21
Actually just deleting xorg.conf would do, I think - because then X will reconfigure itself, and it'll go back to the original working driver.

But I don't know how to delete stuff from the command line..

---

### Post by eUsha on 2007-11-21
As soon as I boot Ubuntu and as soon as the Ubuntu boot screen is done, my screen goes blank. I cannot do any thing but press the reboot button of my system. 

I can load Ubuntu in safe mode. A terminal is open. This is what I typed in the termial and how the termial responded.

When I type nano a text editor opens.
when I type xorg.conf it gives me an error.
when I press Ctrl + Alt + F2 it takes me to a blank screen where on the top left corner there is a cursor blinking.( I had to reboot because I could not do anything)
When I type startx the Screen goes blank just like after starting ubuntu in normal mode. (I had to reboot because I could not do anything)

Is there a way I can reset the driver setting from the disk using the Live CD. Or using the Termial, because I can't do anything. Termial(Safe Mode)  is really the only working part of Ubuntu as of right now.

I also have windows XP installed on a different partition but I can not see Ubuntu from Windows XP.

---

### Post by spiderbatdad on 2007-11-21
The command to enter in the terminal is all one line intended to edit the file /etc/X11/xorg.conf


so the terminal command is    nano /etc/X11/xorg.conf


I dont have a 64 bit machine, but I do have an ATI graphics card, and I have been able to use compiz-fusion satifactorily. Once I got it working, I was  like ok...now I'll turn it off, heh. I had to get the compiz settings manager from synaptic and also found a compiz-fusion icon through google. It allowed me to easily change the windows manger and theme, so that compiz would work.

---

### Post by eUsha on 2007-11-21
nano /etc/X11/xorg.conf

Opens up a blank Document.

---

### Post by eUsha on 2007-11-21
Well to use ATI Graphics card or any graphics card for that matter, does one always have to install open source driver seprately or are the drivers provided with the card sufficient. I guess what I'm asking is that are the drivers for graphics cards good for every operating system or do they target a specific platform.

---

### Post by barney385 on 2007-11-21
Here's a link to the new ATI drivers:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

Supposed to be new and improved. I read an article that AMD is pressuring ATI to be more compatible in the future with the open source community.

We'll see....

:popcorn:

---

### Post by monte48lowes on 2007-11-21
Try this from the command prompt using Recovery Mode:

```
dpkg-reconfigure -phigh xserver-xorg
```

This will reconfigure X.

Mike

---

### Post by stunner on 2007-11-21
> **eUsha said:**
> Well to use ATI Graphics card or any graphics card for that matter, does one always have to install open source driver seprately or are the drivers provided with the card sufficient. I guess what I'm asking is that are the drivers for graphics cards good for every operating system or do they target a specific platform.

Targeted.  Same goes for nvidia cards.  Your choice is to use 'ati' (opensource) or 'fglrx' (proprietary).  There is a line in xorg.conf to specify this - mine says:

Driver   "fglrx"

In your case, you would change the fglrx to ati.  Of course, not having an xorg.conf makes that a little difficult. Are you sure you typed it in correctly (case-sensitive - X11 needs to have an uppercase 'X')?  Also, make sure you are running sudo nano /etc/X11/xorg.conf - the sudo is essential as only root can edit xorg.conf

---

### Post by eUsha on 2007-11-22
THANK YOU VERY VERY MUCH ALL!!!!:)

At least I can now use linux. Yeah the problem was Case Sensitivity. I'm used to window.
I tried downloading the drivers from the link provided by barney385 but I cannot run the installer because it is in some sort of format that can't be read. 

It feels great to be back with Ubuntu after the first date didn't go too well.

---

### Post by ]]]ARGONAUT[[[ on 2007-12-01
I had a similar problem with the wrong drivers for the ATI card and display was too garbled to see images or text clearly.
Couldnt therefore reset so i followed all your helpfull advice and came to the nano screen but that made little sense as i had no idea what it all meant and more precisely how to alter it but it did say that   sudo dpkg-reconfigure -phigh xserver-xorg       was the command to reset the drivers to default.
This works great!!!

---

