---
title: "Mouse stuck and run action fail"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by ofiration on 2007-10-16
Dear Ubuntu members,

Im new to Ubuntu, so please take it easy on me.
I installed the Ubuntu with no problems, it works without the CD.
However I got 2 main problems while im in the Ubuntu.

1.Its seems that there is no respone from my Internet,
so I followed the next actions:

Alt+f2
pppoeconf
Run

But nothing happens after that.

2.my mouse not respone.
I have optic mouse - if Im in windows there is the red light and I can move thse mouse sign over the 
screen and click , however in Ubuntu Its stucks and the red light in the mouse itself not on.

Please Help me,
Thanks in advance,
Ofir

---

### Post by Chilli Bob on 2007-10-16
Hi, and welcome to Ubuntu. 

The answer to your first question is that you have to be logged in as root to run  pppoeconf.  The easiest way is to open a terminal and type...

sudo  pppoeconf

... and it will ask you for your password and you should be up and running. 

However I would avoid this if possible.  The network manager (System - Admin - Network) should detect this for you.  Have you tried doing it the GUI way first?  It might not be hard-core Linux, but it usually works.

I can't help with the second question, but can give this advice.  When asking these questions, please provide some more information on your system, processor type, specs, laptop or desktop etc.  Every little bit helps.

Welcome aboard!

---

### Post by celticbhoy on 2007-10-16
Please supply details of the mouse ie make and model, & version of Ubuntu you have installed.

---

### Post by ofiration on 2007-10-16
Ok, thanks on the fast respone.

What you mean by saying "try with the GUI"?
What is GUI , is there any guide for using it?

Here some details:

ubuntu-7.04-desktop-i386

 My mouse:
```

Wheel Mouse Optical 1.1A USB and PS/2 Compatible
Microsoft

```

 My modem:
```

Model Name: DRUC-U2
Product Name: 802.11g USB 2.0 adapter

```

---

### Post by Chilli Bob on 2007-10-16
The GUI is the graphical user interface, i.e. clicking with the mouse rather than  doing stuff from the command line. You may still have to use the command line from time to time, but I prefer to avoid it when I can.

As far as setting up your internet, have you worked through the documentation?  If not, go to this link..

[https://help.ubuntu.com/7.04/](https://help.ubuntu.com/7.04/)

...and click on "internet". Select your type of modem and you should get step-by-step instructions.  If it still doesn't work, let us know what you did, and where things went pear-shaped.  Be aware that wireless has always been a problem in Linux.  Gutsy might be a bit easier when it comes out in a few days.

good luck

---

### Post by celticbhoy on 2007-10-16
GUI is the graphic interface or the window manager. Try using the Network option in system>Administration

---

### Post by ofiration on 2007-10-16
Oh, but how can I fix the mouse problem, after all with out the mouse I cant do anything.

---

### Post by LowSky on 2007-10-16
Did it work when you used the livd CD?
Did you have it plugged into anther USB port when you installed ubuntu?

try pluging the mouse into another USB port.

---

### Post by ofiration on 2007-10-16
Hi,

I changed the USB plugin and now the mouse is working.


I got into the GUI, where I can see the desktop,brown windows and such.
However I still didnt successed how to activate my Internet.

I run the next commands in the terminal but the output is too long and I cant move it to my
Windows Volume from linux so I need to copy it to a paper and then copy it to this forum
so I cant show you the output.
```

sudo lsusb -v
lspci -v | less
sudo pppoeconf

```

Here more info about my "internet" or how you wish to call it.

```

Network Name: (SSID) 2wite499
Mac Address: 00:0b:6b:6f:f0:63
Ip Address: 172.16.1.36

Board: Prism 802.11 USB adapter
Chipset: GW3887E1020
Firmware Version: 2.05.20.00

```


Thanks for any possiable help.

---

### Post by ofiration on 2007-10-16
OK.

Because I saw that Linux has a problem with Wireless Chips I took the Router from my sister's
computer and gave her the small USB adapter.
Is that aspose to work now?

I still didnt understood how to configure a Netwoek manually.
At the Username,Phone,prefix Dial and all that, I need to fill it all?
Is there any guide to "How to config. your internet?" or something like that?

Thanks again.
Ofir :)

---

### Post by ofiration on 2007-10-19
Hi, im sorry on the bump but here some new info.
I have that little box that gets the data (in wireless way) from the other computer Router.
I took the router and plugin it in to my computer.
I ran Ubuntu and hoped for good, however - still, it didnt recognized it in automatic way.

I took that "little box" again and connected it to my computer and I put the Router in his original
place (the other computer).

Please Help me, is there any hope for wireless internet on linux or not?
Tell me everything you need - just help me make it work.
In every day that passed with this XP system I wanna shot something!!

Thanks in advance,
Ofir.

---

