---
title: "How do i make the laptop search for wireless LAN? and what is with codes?"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by shtewe on 2007-02-15
i am playing around with ubuntu live cd on my laptop and i can't access my wireless network and there is no security on it.  People say put this code in, but how do i do that?  how do i make the laptop search for wireless networks?  That is the onlyu reason i am not installing it because i can't make it connect to the wireless network.  

So confussed! BTW ubuntu is really good except the wireless network configuring thing, confuses the hell out of me!

:confused: :confused: :confused: :confused: :confused:

---

### Post by gree on 2007-02-15
open a terminal, found on the menu.
there you write "iwconfig" to see what your wificard is named. it can be eth1 (like mine is named) , wlan0 or other. you should see 'wireless' or something similar written there.

then you write "sudo iwconfig CARDNAME essid WLANNAME"
(for me it is sudo iwconfig eth1 essid school)

i hope this simple explanation can give some help.
you can try to write "man iwconfig" in the terminal to see more help.

---

### Post by shtewe on 2007-02-16
thanks for getting me into the terminal, but when i type "sudo iwconfig eth1 essid evans" nothing happens, it doesn't say anything.

Still confused

:confused:

---

### Post by Bachstelze on 2007-02-16
That's normal, the card associated itself to the network. Now you can type

```
sudo dhclient eth1
```

to actually connect to it - if your network is using DHCP.

---

### Post by tubasoldier on 2007-02-16
Uh, how about we back up one step. Is your wireless card even supported in Linux? More than likely you have a wireless card that does not work well under linux or needs extra software/drivers installed before it will work properly.

---

### Post by shtewe on 2007-02-16
ok i have put this in the term"inal

"sudo iwlist scan"

it comes up with my wireless network but how do i make it connect to it, it should be so simple from here but it is not?!?!?!!?

---

### Post by Bachstelze on 2007-02-16
Jus as you were told to :

```
sudo iwconfig eth1 essid YOUR_ESSID key YOUR_WEP_KEY
sudo dhclient eth1
```

---

### Post by treesurf on 2007-02-16
I never thought I'd actually be the one giving advice on this forum, but here it goes.  It may be easier for you to do this through the GUI, if that's how you're used to doing things (I am!).  Go to the top of your screen and select system/administration/networking.  Select on wireless connection and then click properties.  You should be able to select your network from the Network Name dropdown menu and then enter your security key.  Click OK and you're good to go (hopefully).


Or you can follow the simple command line code that more knowledgeable folks have posted!

---

### Post by shtewe on 2007-02-16
did what you told me to and it came back with "no DHCPOFFERS recieved"

so it doesn't work with DHC.  dam. this is wat comes up when i scan for wireless

Address: 36:B2:B5:81:66:DE
ESSID:  "Evans"
Protocol : IEEE 802.11b
Mode : Ad Hoc
Channel : 1
Encryption key : Off
Bit Rates 1 mb/s, and so on
Quality = 91/100 signal level 37 dBm
Extra : Last Beacon: 164ms ago


hopefully this helps

thanks for helping me this far

---

