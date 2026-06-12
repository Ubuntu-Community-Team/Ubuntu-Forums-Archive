---
title: "Unable to connect to internet"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by zeitgeist888 on 2008-01-28
I just installed Ubuntu 7.10 from a disc from Ubuntu magazine onto the HD of another computer ( Dell 1501 Laptop AMD 64 ) and I am not able to connect to my DSL wireless network.  I am using a Linksys WRT54G router that is working on other computers in the home.  I have WEP security.

I read some of the documentation and it doesn't seem to make sense.  For example it says to open device manager under "system" and then "administration".  I have no "device manger" listed in sytem and admin tabs.  The closest thing is Restricted drivers manager or network or network tools.

Some other things that hopefully will help me connect.  I tried manually connecting and the 2 computer screen icon near the clock does the blue arrow circle thing but never connects.  I have had the icon of the screens alone, the screen icon with an orange warning triangle and once a vertical bar graph in white that didn't seem to show a signal strength.  Each time I tried double clicking Firefox I only get an Ubuntu looking page but cannot connect to anywhere else if I am connected at all ( I don't think I am ) Firefox is my regular browser and I am fair at windows use if not the best at the lingo.

I am a longtime windows user trying to switch to Linux for the first time and really could use some help.

---

### Post by Ub1476 on 2008-01-28
Hi, I have the WRT54G as well with WEP, and it works brilliant so no problem there. This has something to do with a driver, obviously. Have you seen if there are any available drivers in System>Administration>Restricted Driver Manager? Open the terminal and post the output of this:

```
lspci
```

Don't fear the terminal, it's just faster troubleshooting:)

---

### Post by billgoldberg on 2008-01-28
Some wireless card are supported properly in ubuntu (their makers won't make linux drivers).

There is a program called ndiswrapper that allows you to use your windows xp drivers for you wireless card in linux.

Or you could always buy an wireless usb adapter that is fully linux supported. There is a list somewhere available, google for it.

If you plug in a cable, every should work without any problems.

I'm no expert at this, someone else will be able to help you further.

My wireless card was detected out of the box so I never ran into that problem.

---

### Post by Charcoal1981 on 2008-01-28
Not sure about your main query, but on your point of finding "device manager" try "system>preferences>hardware information" the dialog box this opens is described as "device manager" - it may be what your documentation is refering to.

---

### Post by zeitgeist888 on 2008-01-28
> **Ub1476 said:**
> Hi, I have the WRT54G as well with WEP, and it works brilliant so no problem there. This has something to do with a driver, obviously. Have you seen if there are any available drivers in System>Administration>Restricted Driver Manager? Open the terminal and post the output of this:

```
lspci
```

Don't fear the terminal, it's just faster troubleshooting:)


I did the terminal check you listed and it displays a list of hardware USB controllers from ATI SMBus ATI etc.. it also list the network controller as Broadcom BCM4312 802.11a/b/g rev 1
and Broadcom BCM4401-B0 100Base-TX rev 2

Does this mean it recognizes the hardware but I still need a driver ?

BTW it is a full install over what used to be a Vista Home basic that worked fine before the Ubuntu 7.10 install with nothing else done.

---

### Post by zeitgeist888 on 2008-01-28
I also did an "iwconfig" in the terminal and it shows

  lo  no wireless extensions

eth0  no wireless extensions

eth1  IEEE 802.11b/g   ESSID:" my router name" Nickname: "Broadcom 4311"

         Mode:Managed   Access Point: Invalid
         RTS thr: off   Fragment thr: off

below that is link quality signal level and noise level then RX invalid nwid: 0 RX invalid crypt : 0



Does this info help ?

---

### Post by lmessenger on 2008-01-28
i've had the same trouble with my old desktop computer, and found out that it was just due to the fact the i didn't have the network modem card activated. i could be the same problem for you. also, i've had trouble with network drivers, on my laptop when trying to install 7.04. did the wireless work in live boot (not installed yet)? if not, then it's just a big driver problem that we be time consuming.

---

### Post by zeitgeist888 on 2008-01-28
No the wireless didn't work when I used the live CD but I thought it was because the OS  had to be installed.  My mistake.  Also along the same lines when I opened the network connection ( double clicked on the twin screens near the clock ) in both the live CD mode and after the install I never had a list of available networks like I would see in Vista's network connections on the same computer before the install.  

Would the card be turned off because of the install ?

---

### Post by zeitgeist888 on 2008-01-29
Anyone able to shed some light on this ?

---

### Post by zeitgeist888 on 2008-01-29
Thanks to those that offered help.  I am still unable to connect and am at a loss.  I guess I'll go back to Vista.

---

