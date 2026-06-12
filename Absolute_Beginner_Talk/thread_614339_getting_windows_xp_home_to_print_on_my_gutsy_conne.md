---
title: "getting windows xp home to print on my gutsy connected printer"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by shadowman90 on 2007-11-15
this is really making me mad...

i have an hp psc 1315 (basically 1310) printer connected to my ubuntu 7.10 desktop and the printer works 100% fine locally.

the problem comes when i try to get my xp home laptop to print to it. yes, i have samba installed and i've searched these forums for hours trying to get it working. it used to work, after i spent all of one saturday toying with it, and another time it wouldn't work right away, but i somehow got a login screen to show up, and i logged in with my ubuntu login and it worked fine,

But now i can't even look at the MyShares folder from XP. i can see it, but i can't go in... it says something along the lines of "Network path not found"

you have no idea how frustrated i am and any help you can give me would be greatly appreciated!!

oh and i've been using ubuntu for about a month now, so i'm still kinda noobish.

---

### Post by wolfvorkian1 on 2007-11-15
I did a lot of searching and reading too and the tutorial below is the one that finally solved my problems. The guy writes with a bit of color too, which helps afaic. 

Incidentally, I always get an error message that printing to the printer on my Linux computer won't work, but it is lying. I can print fine. Good luck. 

[http://www.debian-administration.org/articles/425](http://www.debian-administration.org/articles/425)

---

### Post by shadowman90 on 2007-11-16
that didn't work. is there something i can post to help you help me?

---

### Post by shadowman90 on 2007-11-17
bump

i've been toying around and have found that i can't even see the windows machine from my ubuntu but i can see my ubuntu machine from windows, but when i click it it says "you may not have permission to access it from this machine. network path not found"...

i have samba set up just like any guide i've seen...

---

### Post by HermanAB on 2007-11-17
It sounds like you have a basic network connectivity problem.  Fix that, then your other troubles will likely go away.

Soooo, verify your IP addresses.  Ensure that the machines are in the same subnet:
Winfows: ipconfig /all
Linux: ifconfig

Test connectivity with ping:
Linux/Windows: ping ipaddressofothermachine

Use telnet to see whether you can connect to the printer control port:
Windows/Linux: telnet ipaddressoflinuxmachine 631

If the above doesn't work, check your firewall settings.

Cheers,

Herman

---

### Post by ggaaron on 2007-11-17
You DON'T need samba to share your printers, and I recommend you not to use it. Sharing printers is much easier without it. Also using kde or gnome print manager is a bad idea... (i find them slow and unresponsive without a reason, and standard cups configuration also uses graphical interface that is clean and easy) So what I recommend you to do is:

run sudo passwd in a terminal (by default ubuntu doesn't have a root password and you will need one)

open your favourite web browser and go to localhost:631 (you need to have cups installed and running)

In administration check "Share published printers connected to this system"

Add printers

click printers, then your chosen printer, copy the url of the site

On gnu/linux systems when you add new printers then add this link when you add a network printer, on windows find "add printer" and when it asks you for location then paste this link.


I would revert any settings of cups and samba to default ones before doing this. This worked for me quite many times for both gnu/linux and windows.

---

