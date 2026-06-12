---
title: "So close, yet totally confused here"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by utrob on 2007-01-05
It's taken ages to get to the point of a working Ubuntu install 6.0.6 (dual with winxp). 

I'm attempting to use the dellnic.inf file to make my truemobile 1450 usb adapter work. 
So far i understand i need ndiswrapper installed, then i use that to install the dellnic.inf file.

**sudo dpkg -i ndiswrapper-utils-1.1_1.1-5_i386.deb** (supposedly) should install ndiswrapper.

then when i try

**ndiswrapper -i DELLNIC.INF**

I''m told i'm missing various files. The upshot being i need **libc6 2.4.1** and **ndiswrapper-common**.  

I have no internet access within ubuntu so apt-get is unusable?

Any help at all would be awesome!

---

### Post by Sasa_Ivanovic on 2007-01-05
why don't you have internet accses in Ubuntu ? Do you have one in Windows ?
If so you could get the network drivers, install them in Ubuntu and then use that command ...

---

### Post by Bachstelze on 2007-01-05
You installed the wrong package. Instructions for installing nidiswrapper in Ubuntu are [here](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).

---

### Post by utrob on 2007-01-05
Right, must be gettin really close now. I'd seen that link but gone for the wrong option! Ndiswrapper works as does the graphical install. Apparently DELLNIC.INF was already installed (somehow!) but i uninstalled it and reinstalled to make sure it was right.

Just one slight snag... **no hardware present**. Ouch. I'm going to search around but any direction would be awesome.

---

### Post by utrob on 2007-01-05
More information. Ubunutu **does** see my hardware in the device manager screen, however the driver isn't matching with it i guess. 

I had a look in etc/ndiswrapper and found three files. One was DELLNIC.INF and the other two  were config files i presume. One for Dell Truemobile 1300 and one for Dell Truemobile 1450. Could it be possible they're conflicting? 

I don't know how to test, or what to test for that matter. but it seems like **i'm just so close!!**

---

### Post by utrob on 2007-01-05
Even closer now!!

Now i managed to get hardware and driver present.
Network manager doesn't show wlan0 as an option, however ndiswrappers alias is wlan0.

So very close! Any help to finally get internet? Please!!

---

### Post by Bachstelze on 2007-01-05
If you haven't already, do

```

sudo depmod -a
sudo modprobe ndiswrapper
```

Then your wireless interface should show up when you do

```
sudo iwconfig
```

---

### Post by utrob on 2007-01-05
I believe i've done all that, however i'll check now.

---

### Post by utrob on 2007-01-05
There's no wlan0 unfortunatly. 

sudo depmod -a
sudo modprobe ndiswrapper

Both produce nothing (don't know if that's good or bad)

---

### Post by Bachstelze on 2007-01-05
That's normal, does the wireless appear when you do *sudo iwconfig* ?

---

### Post by utrob on 2007-01-05
Sorry, bad communication. 

My first sentance was the result of running sudo iwconfig. No wlan0.

I tried iwlist wlan0 scan but again, no devices found.

Ps. Thanks for the replies :)

---

### Post by Bachstelze on 2007-01-05
No wlan0, right, but anytinhg else ? It might very well be eth1, eth2...

---

### Post by utrob on 2007-01-05
There is an eth2. Through the network manager it appears to be set up correctly, but dhcp returns no results. 

How else could i configure it?

---

### Post by utrob on 2007-01-05
I had a look in etc/network/interfaces  and found that wlan0 and eth1 (both are missing from network manager) had auto eth1/auto wlan0 infront of them whereas eth2 didn't... however i tried changing that, but no change in network manager :(

---

### Post by utrob on 2007-01-05
new update. Everything seems to be ok apart from a complete lack of signal. I'm so confused!

---

### Post by utrob on 2007-01-06
Anyone? Please don't leave me hanging!

---

### Post by petermck on 2007-01-06
Have you gone into System->Admin->Networking and activated the wlan connection? If your still having trouble post the output of iwconfig and cat /etc/network/interfaces here. You use Ctrl-Shift-c to copy in a terminal window, Ctrl-shift-v to paste.

---

### Post by utrob on 2007-01-06
Yes it's all there, all set up correctly (i believe) yet on iwconfig, Quality: 100 Signal 0.

Networking tools shows that eth2 even finds the correct hardware address. etc/iftab shows the correct mac address for eth2 as well.
I'll try and get a full read out but I have no internet acces within Ubuntu. I have to restart and boot into WinXP

---

### Post by utrob on 2007-01-06
Must be dead close now. I ran sudo iwlist eth1 scan and ALL of the nearby routers appeared!! Yet again, slight problem though. i can't seem to connect to them. They all have zero signal and zero noise - surely they must be working if the card can see them?!

---

### Post by petermck on 2007-01-06
Have a look at this guide [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide").
I noticed a section in there about not getting association which sounds a bit like what you are describing.

---

### Post by utrob on 2007-01-06
All solved now. I have a page of scribbled code from various places and i basically just tried different things till it worked! Somehow i'm now successfully using wlan0. Speed isn't the best but at least it works! Thanks for everyones input!

---

