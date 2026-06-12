---
title: "non modem detecting linux"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by edmonder on 2006-09-04
All my computing life I have used windows, but now I wnat to use ubuntu. Linspire and debian will not install hardware or detect its existance properly. In Ubuntu I got the printer working but an operating system that provides no way to install a modem is useless to me ! I have the drivers on cd - I have no idea where the operating system files are in ubuntu or where to find something that lets me try to install the modem. In addition, the video card, and mouse need drivers that are on a cd but there is again no means provided to install them.

I am using a Best data 56k v.92 USB modem model 56usbsl - it's dandy, it's brand new, in windows it works fine and I can go to control panel to mess with the drivers.

Why do I wnat to use Ubuntu ? Because I'm tired of microsoft's attitude that installing something I paid for on a PC I paid for constitutes piracy and because I now have to be careful I don't install something of theirs that phones home or locks me out of a lega operating system. So I would urge you folks to make it easier for new linux users to install your operating system. If you espouse universal access the way you say you do, then I do not see but that you must surpass microsoft. The goal : when a new user pops a cd into  their drive to install Ubuntu, Ubuntu gets installed so everything works, just like windows.

This is not a rant or a flame. I can't even get help without going online because nothing is accessible in ubuntu. I'm not a hacker, and the people who need your operating system should not be forced to write and compile their own in order to use what's installed on their system.

It would be an extreme shame to see linux go away because developers of versions  of linux stubbornly and arraogantly refuse to listen. Microsoft isn't listening either, but they have the market locked up.

Sincerely Edmonder

---

### Post by bluefrog on 2006-09-04
it's not because something is free or very expensive that buying or asking for training is optional.
Companies don't give easily their drivers sources to developers either.

Back to your problem, try the following you may be lucky:

open system / administration / networking
write your password (of the user you are logged in, preferably that's the one you have created during the install)

I assume you want the modem to connect to the internet (as you don't really explain your problem)
select modem connection and click properties.
check "enable this connection" and click on the modem tab.
click on autodetect. you may be lucky and have an answer.
Otherwise contact the company which sells the modem and ask them why they don't make a driver for linux.

James

---

### Post by monktbd on 2006-09-04
> **edmonder said:**
> The goal : when a new user pops a cd into  their drive to install Ubuntu, Ubuntu gets installed so everything works, just like windows.

about supported hardware:
you have to keep in mind that

a) usually hardware developers do not bother at all to supply drivers for windows

b) they also do not bother to open the hardware specifications of their devices to make it easy for linux developers to do so.

not supported hardware in linux = blame it on the hardware developers 


keeping the above in mind it is quite astonishing how much actually works out of the box in linux.

---

