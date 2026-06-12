---
title: "wireless network on ubuntu"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by craig anderson on 2007-06-20
how do I install a wireless network on a ubuntu operating system?

---

### Post by yagood on 2007-06-20
Ubuntu should automatically detect your wireless card and scan for networks. Try clicking on Netowork Manager icon next to the clock and see if any networks show up.

---

### Post by molly_001 on 2007-06-20
The Network Manager referenced above appears near the clock, it looks like "two black monitors" very near each other.

P.S.  You'll need eth0 (probably eth0) to be enabled in there.  (check box)

---

### Post by craig anderson on 2007-06-20
I click on the icon at the top and then clicked on to (conect to other wierless network) on the drop down thing and its now asking for a network name and wierless security. 

so am gessing were it says network name I just type in what my router is called and allso the encripion key in wierless security

---

### Post by molly_001 on 2007-06-20
I'm not sure what you mean by "name of router" however what you do need to type there is the ESSID (SSID) of your Network broadcast.  For instance "Netgear012" or something.

If that does not work, try checking the box for "In Roaming Mode" on the Properties tab of eth0 , then reboot.

---

### Post by craig anderson on 2007-06-20
ok all give that a try :D

---

### Post by craig anderson on 2007-06-20
not haveing any luck at all I typed in my routers ESSID and its come up with no networks avalable

---

### Post by yagood on 2007-06-20
If you set wireless card in Roaming Mode like molly said, it should detect available wireless networks and you should be able to select the one you want from Network Manager context menu.

---

### Post by craig anderson on 2007-06-20
It is on roaming mode but it still can't find my wireless network or any other network or that matter :?:

---

### Post by yagood on 2007-06-20
If you left-click on Network Manager icon, what exactly are the entries in the context menu?

---

### Post by craig anderson on 2007-06-20
enable networking and enable wireless and they both have a tick next to them something like this

../
\/   enable networking

../
\/   enable wireless

(ignore the dots)

---

### Post by yagood on 2007-06-20
That's when you LEFT click?

---

### Post by craig anderson on 2007-06-20
> **yagood said:**
> If you left-click on Network Manager icon, what exactly are the entries in the context menu?

but that what you said ?

---

### Post by yagood on 2007-06-20
Yes, but that's strange to me, I get "Enable networking / Enable wireless" after right click, after left click I get list of networks, hmm...

EDIT: What version of Ubuntu are you using?

---

### Post by craig anderson on 2007-06-20
7.04 festy faun

---

### Post by yagood on 2007-06-20
Also please post output of the following command typed in the console:

```
sudo iwlist scan
```

---

### Post by yagood on 2007-06-20
Also please post output of the following command typed in the console:

```
sudo iwlist scan
```

---

### Post by craig anderson on 2007-06-20
what do you mean buy command typed in the console (sudo iwlist scan) I have no idea what that means ???

---

### Post by yagood on 2007-06-20
Go to Applications > Accessories, launch Terminal and type this command. Then post the output here.

---

### Post by craig anderson on 2007-06-20
craig@craig-desktop:~$ sudo iwlist scan
lo        :interface doesn't support scanning .

eth0   :interface doesn't support scanning .

eth1   :interface doesn't support scanning : no such device

---

### Post by yagood on 2007-06-20
It looks like there's something wrong with wireless card configuration then, because manual scan that you just did should reveal available networks.

Try going to System > Administration > Network and look for "eth1" under "Connections". Make sure it's enabled (checkbox next to it is ticked) and it says "Roaming mode enabled" under "Wireless connection (eth1)".

---

### Post by molly_001 on 2007-06-20
In Feisty Fawn on my wireless controller I have found,
that if a list of wireless networks nearby is detected,
then go to the radio button for the found network of choice,
left click on that radio button, and it will attempt to make a connection
assuming valid WPA/WEP credentials.
Note:  I have to do this (left click on radio button) even for my default network,
every load up of Gnome.

---

### Post by yagood on 2007-06-20
> **molly_001 said:**
> In Feisty Fawn on my wireless controller I have found,
that if a list of wireless networks nearby is detected,
then go to the radio button for the found network of choice,
left click on that radio button, and it will attempt to make a connection
assuming valid WPA/WEP credentials.
Note:  I have to do this (left click on radio button) even for my default network,
every load up of Gnome.

Yes, that's how it works on my PC too, but it seems that Craig doesn't have list of networks after left click and "sudo iwlist scan" output revealed that there's a problem with eth1 interface.

---

### Post by craig anderson on 2007-06-20
I removed one of my network cards in the hope that one of them might be busted but to no avail what so ever.

went to Terminal typed in (sudo iwlist scan) and I now got

lo :interface doesn't support scanning .

eth1 :interface doesn't support scanning : no such device


so am maybe thinking now that my wireless card is f**ked all together now

---

### Post by wieman01 on 2007-06-20
What wireless card do you have and what is the version number?

---

### Post by craig anderson on 2007-06-20
my wireless card is a (bt voyager 1040)

---

### Post by molly_001 on 2007-06-20
> **yagood said:**
> Yes, that's how it works on my PC too, but it seems that Craig doesn't have list of networks after left click and "sudo iwlist scan" output revealed that there's a problem with eth1 interface.


You're right -- I am sorry -- I misread and "crossed" my posts (and my eyes) for the yagood post and the craig post, regarding left clicking and finding networks present.

Sorry to you both for the confluxtion.

---

### Post by wieman01 on 2007-06-20
> **craig anderson said:**
> my wireless card is a (bt voyager 1040)
As far as I can tell it has got a Broadcom 4306 chipset. So I don't think it works out of the box.

This is a good place to start from:

[http://ubuntuforums.org/showthread.php?t=405990]("http://ubuntuforums.org/showthread.php?t=405990")

---

### Post by MrKlean on 2007-06-20
I didn't read all the posts,  but did you try ndiswrapper...maybe you need windows drivers installed ??  It was simple to set up on my other puter ..

---

### Post by craig anderson on 2007-06-21
The story so far 

The network card I was useing before ( bt voyager 1040 pci adapter) it had Broadcom riten all over it like what Wieman01 said so rather than getting it to work I had the opinion of swaping it from my other computer. I have two computers one with windows and one with ubuntu (obviously) so my ubuntu machine now has a (ralink turbo wireless card) and its found all other networks in the area including mine were I live but I now have the problem that I click on the network of choice and it says its connected but when I click on firefox and go to google It says it can't find sever. or to put it short am still not connected even all tho it says I am connected.

---

### Post by craig anderson on 2007-06-22
bump

---

### Post by craig anderson on 2007-06-22
[size="4"]sorted!![/size]

---

### Post by yagood on 2007-06-22
Great!

Could you post a short description of your solution? People having the same problem in the future will be able to benefit from it. Thanks.

---

### Post by craig anderson on 2007-06-22
baseicly I burnt imige of ubuntu 7.04 on to another c.d at 4x righting speed then reinstalled ubuntu on to my machine then when what was done I changed network settings and changed wireless from roman mode to manual mode typed in my networks (ESSID) and from there on I went to firefox and typed in [www.google.co.uk](www.google.co.uk) and that was it.

---

