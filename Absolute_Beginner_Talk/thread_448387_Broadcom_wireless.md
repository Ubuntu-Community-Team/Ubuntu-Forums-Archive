---
title: "Broadcom wireless"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by jskeys on 2007-05-19
First let be than all of you who put in your time helping us newbees out.  I have spent hours reading posts and have been very impressed with your understanding all of our problems.  I hope one day to be able to give back to the community too.  For now I can only say that your efforts are the best ad for Ubuntu that exists.
  I am using 6.10 on an Acer Aspire 1712 laptop with a broadcom 4306 wireless card.  I am not  a programing type and am absolutely new to Ubuntu.  Everything is working fine except the wireless card and there seems to be a slight problem with the mic when I try to use headphones (mic cuts in and out from time to time).  I'm not worried about the mic, but do need the wireless.  I'm in Monrovia, liberia and have Lan at work (everything is ok with thw Lan) but have wireless in my quarters (no go there).  I am still running dual boot because windows works fine with the wireless. 
 I have tried to follow steps to get the wireless installed.  When I first loaded 6.10 it recognized the card was there but would not work.  I have blacklisted the bcm43xx drivers.  When I check the device manager it still shows my Broadcom wireless is there in the list.  When I check Network settings it does not show my wireless anymore.
  I'm sure there is something simple that I am doing wrong and you guys who know what you are doing will spot it I'm sure.  Remember, I'm not the brightest bulb on the tree and you may have to resort to mono-silabic  words for me.  I have tried to followed the instructions "How to: Broadcom 4306 With Ndiswrapper 54 Mbps"  I have the drivers bcmwl5.inf and bcmwl5.sys on my desktop and the bcmwl5a.inf and bcmwl5a.sys on the desktop in a folder named drivers.  As you can see I tried both. When I get to Step 6. sudo ndiswrapper -1/home/quentin/desktop/bcml5.inf   this is what I get:

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-da               Write module alias configuration for all devices
-di               Write module install configuration for all devices
-v                Report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
john@john-laptop:~$ sudo ndiswrapper -i /home/john@john-laptop/desktop/bcmwl5.inf
Installing bcmwl5
couldn't copy /home/john@john-laptop/desktop/bcmwl5.inf at /usr/sbin/ndiswrapper-1.8 line 144.
john@john-laptop:~$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
john@john-laptop:~$ lspci | grep broadcom\ corporation
john@john-laptop:~$ sudo ndiswrapper -i /home/john/desktop/drivers/bcmwl5a.inf
Password:
Installing bcmwl5a
couldn't copy /home/john/desktop/drivers/bcmwl5a.inf at /usr/sbin/ndiswrapper-1.8 line 144.
john@john-laptop:~$

---

### Post by AAM on 2007-05-19
hi jskeys!

let's see if you can't get some help for this. Firstly
> sudo ndiswrapper -1/home/quentin/desktop/bcml5.inf is incorrect! You used a 1 (one) not an i ("eye").

Secondly, when you do the bcmwl5.inf install, do you have the bcmwl5.inf AND bcmwl5.sys files in the same directory? 

Thirdly, I don't understand what this is? >  john@john-laptop:~$ sudo ndiswrapper -i /home/john@john-laptop/desktop/bcmwl5.inf It looks like you have called your home directory ('john') something else ('john@john-laptop'). This is obviously a problem. I looked through the HOWTO you listed and it all looks correct. Try again an use copy and past rather than typing yourself.

---

### Post by jargoman on 2007-05-29
Try my tutorial. I've only tested it with the Broadcom 4318 but it should work with the 4306.

leave me a post on this thread if it works and I'll change my site to the Broadcom 4318/4306 how to. I've done some searching and I think it will work for you.

You should be able to copy and paste the commands into your terminal!

[http://freeshells.ch/~jargoman/ndiswrapper.html](http://freeshells.ch/~jargoman/ndiswrapper.html)

---

