---
title: "driver present but Hardware NOT present"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by zatross on 2006-01-16
Happy new Year all!

I've spent the last 2 weeks visiting several forums with the hope of finding some help in getting to the internet via my Breezy installation on a HP Vectra via a Belkin wireless F5D7050 USB stick. Here is a summary of my headache

1) After reading everal threads, I ended up installing ndiswrapper-1.7 and reloaded the driver file from the belkin site now when I do 

**ndiswrapper -l**

I get driver present .... I know it should also say Hardware present but this is not the case.

2) running **'sudo iwconfig wlan0'**, I get

- *wlan0 No such device*

3) One observation I've made: If I restart the machine without disconnecting the USB port first, it hangs.

Please help. I am newbie to Linux and I am supposed to be building a computer centre in a village in Africa for a charity. I choose Edubuntu because it seem to have all we need! I am giving myself a crash course before I get there in 4-weeks time to prevent letting a lot of children down! :(

---

### Post by az on 2006-01-16
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Your card is reposrted to work - There are two entries (19 and 20) which describe two different chipsets Prism and Realtek)

You should try to remove any version of ndiswrapper that you installed yourself and just use the one that ships which Breezy

do

ndiswrapper -l
and then
sudo ndiswrapper -e (driver)
(remove all the drivers that are installed)

sudo apt-get install --reinstall linux-image-2.6.10-(whatever version you are running) as well as reinstalling ndiswrapper-utils.

Then find out the chipset you have and fetch the most recent .inf file (windows driver - the one that came with the card may not be the most recent one)
What happens then?

Also, if it is the prism chipset I think it is supposed to work out-of-the-box without ndiswrapper since the prism54 driver is included in the kernel.

---

### Post by Stealth on 2006-01-16
There seem to be 2 version of this USB key, do you know which one? One of em is based off of Prism and the other (a lot easier to install) is an RT2500 based chip. What was the name of the driver's .inf file?

<edit>Geez, I'm too slow, azz already explained my post ^_^</edit>

---

### Post by zatross on 2006-01-16
Thanks Guys!

From the sys file I got from the XP install directly, I know it's a Prism.

I'll try removing the ndiswrapper to see what happend.
btw, I initially played around with Driverloader but I haven't removed that yet; could there be a conflict? I tried using DL to load the driver and it failed; it did work before, though! what woul dbe the best way to remove?

Cheers

D

---

### Post by az on 2006-01-17
[QUOTE=zatross]I initially played around with Driverloader but I haven't removed that yet; could there be a conflict? 
D[/QUOTE]
Yes.  Why pay for milk when you can get the ndiswrapper cow for free?

I don't know how to remove DriverLoader...

---

