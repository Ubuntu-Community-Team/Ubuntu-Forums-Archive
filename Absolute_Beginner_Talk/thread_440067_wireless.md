---
title: "wireless"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by alexh on 2007-05-11
Ok i have just installed Ubuntu and it seems to be working fine but i am having some difficulty connecting it to the internet. I have gone into the the network settings and it has already discovered my wireless card and can find local wireless networks but they all have 0% signal strength and i cannot connect to mine (or any of my unprotected neighbours). I have even disabled the security on mine to see if that was the problem but it has not made any difference and i still cannot connect to it. 

Does anyone have any idea what is wrong and how it can be fixed?  

Cheers

---

### Post by Bachstelze on 2007-05-11
What kind of wireless card do you have ?

---

### Post by alexh on 2007-05-11
It is a Belikn PCI, wireless G  one, that is a couple of years old now, i have no idea what model off the top of my head though i could find out if needs be.

---

### Post by Kobalt on 2007-05-11
Can you please post the output of the command line *lspci* then ?

---

### Post by alexh on 2007-05-11
right i have done that and given that i am writing this on the laptop i would rather not type the whole thing out but the bit i assume the bit you are after is this:

01:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-iPCI (rev 01)

is that any help?

---

### Post by Bachstelze on 2007-05-11
Now

```
lspci -n | grep 01:08.0 | awk '{print $3}'
```

---

### Post by alexh on 2007-05-11
That gives:

1814:0201

---

### Post by Kobalt on 2007-05-11
I believe I read somewhere that there was a little problem with Feisty's built-in drivers for RT2500 chipsets... This might be helpful : [http://ubuntuforums.org/showthread.php?p=2323797](http://ubuntuforums.org/showthread.php?p=2323797)

---

### Post by alexh on 2007-05-11
Right i just read through that page and to be perfectly honest i am no better off for it. Is there a slightly less jargon full version for those of us who are less technically aware? Sorry to be so pathetic but this is my first foray into the world of linux and i really don't know much about it.

---

### Post by aeiah on 2007-05-11
basically i think you'll need to blacklist what is mentioned in that thread, this will disable the faulty drivers, and then you'll need to install the rt2500 drivers. there are guides for this on this forum, and there may even be a .deb for it (which you'd just double click to install). ive installed this driver several times myself and whilst it can be a pain in the *** to install if you havent got a wired connection, it isnt too bad if you can get the internet via ethernet (to download dependencies).

it isnt too complicated. i did it first when i was new to linux and it was a bit of a challenge, but there is a clear howto somewhere on this site

---

### Post by alexh on 2007-05-11
I can probably work it out and i can wire up the internet it will just be a pain as the rouer is not that close to the computer so i will need a fairly long cable. 

Cheers for the help guys i wil give it a go and if i have any problems i know where to come.

---

### Post by Austin_KW on 2007-05-11
The installed driver should work
post your /etc/network/interfaces;

FYI; here is the relevant part of my  /etc/network/interfaces
```

auto ra0
iface ra0 inet dhcp
    pre-up ifconfig ra0 up
    pre-up iwconfig ra0 mode managed
    pre-up iwconfig ra0 essid GabbyNet
    pre-up iwpriv ra0 set EncrypType=TKIP
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwconfig ra0 essid GabbyNet
    pre-up iwpriv ra0 set  WPAPSK="xxxxxxxxxxxxxxxxxxxxxxxx"
    pre-up iwconfig ra0 essid GabbyNet


```

---

### Post by alexh on 2007-05-11
happy to but how do i bring up my ect/network/interfaces?

---

### Post by Austin_KW on 2007-05-11
You are probably goint to need to edit it so;
alt-F2 ;to bring up the run command prompt

then enter "gksudo gedit /etc/network/interfaces"
and click on run.

---

### Post by alexh on 2007-05-11
Right ok that gives me: 
```

auto lo
iface lo inet loopback

auto eth1
i face eth1 inet dhcp

auto eth2
i face eth2 inet dhcp

auto wlan0
i face wlan0 inet dhcp



iface eth0 inet dhcp


iface ra0 inet dchp 
wireless-essid Ed

auto ra0
```

---

### Post by alexh on 2007-05-11
i have just got to go and get a suit fitted form my mates wedding so i wont be able to reply for a cuple of hours but i would really like to get this sorted today so will be back later.

Cheers

---

