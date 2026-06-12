---
title: "No internet connection."
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by kwjaxon on 2006-03-13
I am new and have a dual boot.  I am unable to get an internet connection.  May not know enough to use Ubuntu but sure would love to try.  What is the first thing I need to do and maybe a source for some good help.  Thanks.

---

### Post by malacandra on 2006-03-13
Hard to pinpoint without knowing what kind of internet connection you have.

I'll guess broadband since you're actually running Ubuntu and have installed it.

Open a terminal (for q quick terminal hit ALT+F2 and enter **xterm**
type **sudo ifconfig** (will ask for password)

That will list your network devices. On a desktop computer you will probably have two: 
eth0  and lo; you may have something like wlan0 if you have a wireless card.

Make sure it shows eth0 (or whatever number it may be). If not, then it's not seeing the network card at all. 

Otherwise, use these two commands:

**sudo ifconfig eth0 up**   this activate the network card
**sudo dhclient eth0 ** that will get your DHCP address.

You can run ** sudo ifconfig ** again and see if you have a DNS address.

You should, and you can start surfing. 

Let us know how that works. If not we can go from there.

---

### Post by Koybe on 2006-03-13
It depends how are you connected to the internet? Directly to a modem? to a router?

You need to give more informations if you want to get help ;)

---

### Post by Iowan on 2006-03-13
[QUOTE=kwjaxon] What is the first thing I need to do and maybe a source for some good help.  Thanks.[/QUOTE]
[http://ubuntuforums.org/forumdisplay.php?f=100]("http://ubuntuforums.org/forumdisplay.php?f=100")  has a lot of good How-to's. 
 [http://www.howtoforge.com/]("http://www.howtoforge.com/") also has good reading - most is not Ubuntu-centric.

---

### Post by kwjaxon on 2006-03-13
Sorry Guys, have a dial up modem.  Lucent Winmodem model.

---

### Post by Brunellus on 2006-03-13
[QUOTE=kwjaxon]Sorry Guys, have a dial up modem.  Lucent Winmodem model.[/QUOTE]
I linked you to the WinmodemLucent wikipage on the other thread.  did you read that, or did you just post another one?

---

