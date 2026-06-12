---
title: "Can't connect to wireless with 11.04"
date: 2011-06-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Bag of Paper on 2011-06-04
Recently updated from 10.04 to 10.10 and then 11.04. Since updating to 11.04 i can't connect to my wireless internet, and when it very occasionally connects, it doesn't work and pages won't load. I had this problem when i first installed ubuntu on my asus eepc 1000HE but can't remember how i resolved the situation! It's not the router as all the other computers in the house work fine.
thanks :)

---

### Post by gangov on 2011-06-04
Look in your BIOS if the wifi is turned off.  Otherwise you can see this [http://www.beakkon.com/geek/how-to/fix-wireless-internet-connection-problem-on-ubuntu-10.10]("http://www.beakkon.com/geek/how-to/fix-wireless-internet-connection-problem-on-ubuntu-10.10") , or open terminal (ctrl+alt+T) and type in "rfkill unblock all" (without quotes)..

---

### Post by Bag of Paper on 2011-06-07
tried all 3 of those things and none worked :S

---

### Post by Bag of Paper on 2011-06-08
bump???

---

### Post by Bag of Paper on 2011-06-12
still no dice, if i can't fix it i'm going to go back to windows as i'm annoyed i have to use my desktop everytime i want to use the internet now.. ???????????????

---

### Post by Bag of Paper on 2011-06-15
anyone?

---

### Post by kyteflyer on 2011-06-15
> **Bag of Paper said:**
> anyone?

I had this issue with 10.04 on my 1001HA.  I simply reverted to 9.10 until 10.10 was released.  In your shoes, I would revert to 10.10 and wait for 11.10

---

### Post by Bag of Paper on 2011-06-19
i have to do a complete re-install then hey? may as well just put 7 on it if i'm going to do that, i don't want to have to do a re-install :(

---

### Post by Plumtreed on 2011-06-19
There are many examples of this problem in the 'wireless & networking' part of this forum. Some may even relate to your specific hardware.

I have an Acer laptop and found it necessary to remove all reference to the old driver and install the recommended driver and components. 

I'm sure you will find a specific example of how to fix your eeePC in the networking section.

---

### Post by reqqq on 2011-06-25
maybe you can try some of these

[http://ubuntuforums.org/showthread.php?p=10750214#post10750214](http://ubuntuforums.org/showthread.php?p=10750214#post10750214)

[http://ubuntuforums.org/showthread.php?t=1745354&highlight=natty+wifi+issues](http://ubuntuforums.org/showthread.php?t=1745354&highlight=natty+wifi+issues)

searching something you can find as i did with my wifi freezing problems
hope helped

---

### Post by bdoe on 2011-06-25
> **Bag of Paper said:**
> i have to do a complete re-install then hey? may as well just put 7 on it if i'm going to do that, i don't want to have to do a re-install :(

If you want to put Windows 7 on your computer as a means of fixing your problem, then please feel free to do so. Nobody is going to stand in your way or try to stop you.

On the other hand, if you are willing to work with us, then we'll do everything we can to help you out in getting your Ubuntu issues ironed out. You can start by telling us a little about your system, such as what kind of wireless card you have in the thing. You can use the lspci command to find out, and can even paste the output of lspci to your reply here.

---

### Post by Bag of Paper on 2011-06-26
I'm very happy to work with you guys, i was getting frustrated that i couldn't use my netbook for the means in which i intend to use it (general internet stuff!). I'm good with windows but ubuntu is a whole new world for me and i struggle with all the inputting to terminal and so on and i tried a few solutions someone suggested on the other page to no avail

> 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Network controller: Ralink corp. RT2860
03:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)


There is all my info

---

### Post by bdoe on 2011-06-27
Ick. I've seen nothing but problems around here with Atheros cards on Natty. Unfortunately, I know next to nothing about them. All I can offer are a few pointers I've seen around these forums for those running Atheros cards on Natty.

Edit: Scratch all that... I just realized your ethernet card, not your wireless card, is Atheros. You might have some luck trying the suggestions in this thread: [http://ubuntuforums.org/showthread.php?t=1744994](http://ubuntuforums.org/showthread.php?t=1744994)

---

### Post by finnbuntu on 2011-07-10
My Eee PC 901 has the Ralink RT2860 and I had the same problem. I fixed it by blacklisting the old driver:

```
sudo gedit
```

Then I located /etc/modprobe.d/blacklist.conf and added a new line saying blacklist rt2800pci. I saved the file, then I rebooted the Eee PC.

```
sudo reboot
```

Everything worked fine after. Hope this solves your problem,
Finnbuntu

---

