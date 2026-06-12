---
title: "Total Newbie fighting with USB Modem driver"
date: 2005-05-26
forum: Absolute Beginner Talk
---

### Post by locovich on 2005-05-26
Hi All,

I've recently downloaded and managed to install the ubuntu 5.04 "distro". I bought a new AMD 64bit machine so since I was reinstalling all over, I thought is a good time to try Linux.  \\:D/ 
Installation is a breeze and went by with no problems at all, now, I boot up my machine and end up in the Ubuntu desktop fairly fast and even with the choice to boot up with XP, which I still use to work from home (at least until I get all the apps I need installed in Ubuntu).

The thing is my ISP provided me with a Conexant USB ADSL Modem.  ](*,) 

Now, I've tried the Google approach, and found several interesting and "at first sight" useful links, like:
[http://sourceforge.net/projects/accessrunner](http://sourceforge.net/projects/accessrunner)
[http://mx.grulic.org.ar/archiver/html/grulic/2004-12/msg00499.html](http://mx.grulic.org.ar/archiver/html/grulic/2004-12/msg00499.html)
[http://www.ubuntu-es.org/node/1849](http://www.ubuntu-es.org/node/1849) (Spanish is my first language)

But all this tutorials and documentation are not intended for Ubuntu users with the Kernel version the 5.04 uses.

So, here I am, asking for help, since I'm such a newbie, I don't even got to compile the driver, since "make" does not work in Ubuntu, I read in some place that the build-essentials are required but don't know how to install that either.

I have this file in there and extracted, but I don't know how to run the build file in it, and I think it references files that are not there  [-X 
usbatm-20050216.tar.bz2

So, please help, could someone please guide my inexperienced hand through this unfamiliar OS?

Thanks a lot.

Locovich

---

### Post by N'Jal on 2005-05-26
What error messeges appear when you type make? Does it say unable to make target exiting or make not found.

If the former find someone that knows more than me, if the latter you probibly don't have make installed. To do this type 
> sudo apt-get install make
I presume that make is the name of the package, but i really don't know. It seems logical to call the package make, make. Else try installing gcc like above but gcc instead of make

---

### Post by locovich on 2005-05-27
N'Jal,

Thanks a lot for your reponse, I'll try this out today, once I get back home. 

I'll post the progress then.

Best!
Locovich

---

### Post by locovich on 2005-05-28
Ok, progress update.

The errors that where displaying after I tried to do make originally are:
root@Locovich:/home/locovich/Desktop/drivers/usb/atm # dir
cxacru.c  Kbuild  Kconfig  usbatm.c  usbatm.h
root@Locovich:/home/locovich/Desktop/drivers/usb/atm # make usbatm
cc     usbatm.c   -o usbatm
make: cc: No se encontró el programa (Program not found)
make: *** [usbatm] Error 127
root@Locovich:/home/locovich/Desktop/drivers/usb/atm # make cxacru
cc     cxacru.c   -o cxacru
make: cc: No se encontró el programa (Program not found)
make: *** [cxacru] Error 127

After this I tried what was suggested and run:
apt-get install build-essential

That installed something  :)  , and then tried the make again, this time the output was a very very long list of errors  :roll:  , I'm pasting just the first part, let me know if you need the entire thing in order to determine what the problem is.

root@Locovich:/home/locovich/Desktop/drivers/usb/atm # make cxacru
 cc     cxacru.c   -o cxacru
In file included from /usr/include/linux/jiffies.h:8,
                 from /usr/include/linux/sched.h:12,
                 from /usr/include/linux/module.h:10,
                 from cxacru.c:30:
/usr/include/asm/system.h: En la función `__cmpxchg':
/usr/include/asm/system.h:249: error: `LOCK_PREFIX' undeclared (first use in this function)
/usr/include/asm/system.h:249: error: (Each undeclared identifier is reported only once

finally I run lsusb just to be sure the device is there, and it is:
Bus 001 Device 003: ID 0572:cb00 Conexant Systems (Rockwell), Inc.

Please let me know what's going on (if you can tell with this info) and what my options are... I think this driver package is the closest available for this kernel, the only 2 options I see, are: 
       1 - Go back to the previous Kernel version (2.4) and try the older driver package.
       2 - Change the modem to an ethernet modem.

Thanks very much for your help,
Locovich

---

### Post by locovich on 2005-06-01
Hi All,

Someone has any idea on what the problem could be here? I've posted the output above.

Please let me know if I can have hope with this modem.  ](*,) 

In the other hand, when installing Ubuntu the net board (in board realtek) was not detected, does anyone use this mobo? ASUS K8S-MX  :-| 

If I have to buy an ethernet modem, I need to be sure the net board is supported by Ubuntu. Right now it is not detected, but it is not pluged either, as a newbie, I'd like to know if that's the reason why it's not detected or if this board is not suported by Ubuntu.  :? 

The realtek chipset is: Realtek RTL8201CL 10/100 LAN PHY

Thanks!
Locovich

---

### Post by CJShiami on 2006-11-07
I'm having similar driver issues after my recent install.

My story sounds rather similar actually.  Just got a new computer, and decided to dip my feet, so to speak, into Linux.  I went with Ubuntu based on a friend's recommendation.

Install went fine.  However, Ubuntu 6.10 does not recognize any of my onboard components except for the video.

I have the same Ethernet Chipset on this machine as yours as well.  

I got the AM2NF6g-VSTA board, with the Realtek TRL8201CL ethernet card.

The ethernet card is what's really bothering me. 

Without a way to get internet access while IN ubuntu, I have to boot in and out of windows to try to get anything to work.  I can't get any additional help inside Ubuntu either. 

If anyone knows of a decent way to get the drivers for this board, or even one for this ethernet chipset, into ubuntu, I'd really appreciate it.


- Carla

---

