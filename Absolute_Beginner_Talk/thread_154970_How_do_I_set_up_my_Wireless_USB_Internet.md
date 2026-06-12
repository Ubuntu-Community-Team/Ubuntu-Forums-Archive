---
title: "How do I set up my Wireless USB Internet?"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by Flamez on 2006-04-04
I dont understand how to install anything, so could someone give me a step by step guide on how to set it up. Ive asked someone before but I dont understand it because I just started Ubuntu and wanna try to see if its good for me.
Also how hard is it to adapt from windows to linux?

---

### Post by carlosqueso on 2006-04-04
I'll answer your questions backwards.  First, it is an effort to adapt from Windows to Linux, but if you are willing to keep an open mind and unlearn what you've learned from Windows, you will find that it very well may be worth it.  

As for your USB wireless card, what kind of card do you have? Please open a terminal and type lsusb and post the output.  Once we get that, we'll be able to help you much more easily.

---

### Post by Flamez on 2006-04-04
Im at my school right now, so Ill post all that tonight once I get home. I have a Belkin one, not sure the model number, and I have heard that the belkin set have a wierd atmel or something, which is a huge hassle to use. I do wanna learn about Linux, since I hope to soon learn to become a computer programmer, and since Im only 16 I figured might as well try to start now.

---

### Post by Flamez on 2006-04-04
I just checked it out, its a Belkin 7050 USB Adapter

---

### Post by Flamez on 2006-04-04
I got this from typing in lsusb:

Bus 001 Device 002: ID 050d:705c Belkin Components
Bus 001 Device 001: ID 0000:0000

---

### Post by carlosqueso on 2006-04-04
You'll need to use ndiswrapper to install your driver, and methinks you'll need the windows drivers from the CD.  According to the ndiswrapper website, you need to install the windows drivers to your WINDOWS pc and grab the .sys and .inf files from the directory that the installer creates.  Then, copy those to your computer in a place where you can find them.  

Next you need to install the ndiswrapper-utils package with ```
sudo apt-get install ndiswrapper-utils
```, assuming, of course that you have a wired internet connection working. 

Once you get that, navigate to the directory with your drivers that you copied from windows and type ```
sudo ndiswrapper -i <INF FILE>
sudo modprobe ndiswrapper  [code] where <INF FILE> is the name of the inf file you copied from windows.  Please remember that you must be in the directory with your drivers, and that linux is CaSe SeNsItIvE!  Then type [code]sudo ifup wlan0
``` and it should work.  To get it to come up at startup, type ```
sudo ndiswrapper -m
```.

Of course, things are rarely this easy, so if you have any problems, post back and people here (possibly me) will do our best to help.

---

### Post by Flamez on 2006-04-05
Well whenever I type anything refering to wlan0 it always slows the comp down and nothing happens.

---

### Post by carlosqueso on 2006-04-05
I had the same problem at first...I'm assuming that you get it set up up to that point and ndiswrapper works.   You may need to compile a new version of ndiswrapper, or you may need to find another driver.  I'd give the driver here [http://www.belkin.com/support/download/downloaddetails.asp?download=1379&lang=1](http://www.belkin.com/support/download/downloaddetails.asp?download=1379&lang=1) a try.  Also...do you have an smp-enabled kernel? It looks like that card has problems with those.

---

### Post by Flamez on 2006-04-05
Ive been using the NDIS that comes compiled with Ubuntu 5.10, and I dont know how to install a new version, everytime I try something messes up. I dont know what smp means exactly. Ill check everything out when I get home.

---

### Post by Flamez on 2006-04-05
I tried installing that to my Windows pc, and looked at the folder I installed it to, but theres no inf files.

---

### Post by carlosqueso on 2006-04-05
hmmmm....I'm not 100% sure about this, but from some searching on product pages, there seem to be 4 different versions of your card. 1000,2000,3000, and 4000.  Which one do you have?

[http://www.zydas.com.tw/downloads/download-1211.asp](http://www.zydas.com.tw/downloads/download-1211.asp) --may contain the windows, and possibly linux drivers for the 4000 

[http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm) --contains the Ralink drivers used for earlier versions of the card...I'm not sure which one you would use, try the RW2571 drivers, as they seem to be closest to what I've found

I don't know if either of these will work, I don't have the same card as you, but good luck.

---

