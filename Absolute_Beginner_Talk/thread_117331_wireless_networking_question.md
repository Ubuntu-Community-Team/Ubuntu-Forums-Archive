---
title: "wireless networking question"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by jefeweiss on 2006-01-14
I installed Ubuntu on my Toshiba Satellite 2545 CDS.  This is the first time I have ever installed, or even used Linux on any computer. Overall it went pretty well, I had a video problem I got sorted out.
Now I am trying to get a wireless network set up.  My wireless card is a Linksys WPC54G ver 3.  I have installed the ndiswrapper that comes in the repository.  I installed it with the drivers that come on the CD as mentioned on the wiki for wireless cards.  The card doesn't work.  If I do iwconfig it shows my card as wlan0, but if I do ifconfig it only shows the lo.  I'm at a loss for what to try next.  I could try uninstalling it and trying again with a newer version of ndiswrapper and an updated driver, but I didn't see directions for unistalling.  I also think that if the drivers were the problem it wouldn't recognize the card in iwconfig.  

Any suggestions?  If you need anymore info I can give it, but I didn't cut and past things because I can't use the net on the laptop, I'm on my Windows desktop.

Thanks

---

### Post by carlosqueso on 2006-01-14
do ```
 lspci 
``` in the terminal to see what the system thinks that your wireless card is. Then search for an updated driver for THAT card (ether win or lin).  If you find a windows driver, uninstall the one that you have and install the new one.  You can also try ```
 ifup wlan0 
``` and see if it works.

---

### Post by Zelut on 2006-01-14
You also may need to 'activate' your card under System > Admin > Networking.

(this is assuming **ndiswrapper -l returns: driver present, hardware present** and that you've done **sudo modprobe ndiswrapper**)

---

### Post by jefeweiss on 2006-01-14
When I do ifup wlan0 it says:
ifup:interface wlan0 already configured

ndiswrapper - l returns

driver present, hardware present.

I have activated wlan0 using system admin networking.

When I ping I get network is unreachable.

---

### Post by Zelut on 2006-01-15
does iwlist show any available networks or maybe installing network-manager?  That is weird.. 

do you have MAC filtering turned on with your router AP?  I can't think of anything else that might deny your connection..

---

### Post by lindejos on 2006-01-15
I have a netgear wifi card and I used madwifi instead of ndiswrapper.  You might want to check it out.

---

### Post by jefeweiss on 2006-01-15
I'm going to reinstall the whole distribution in twxt-mode and take some notes on what happens.  I'm probably going to try my hand at the latest version of ndiswrapper after that.  If I still have a problem I'll post it to the regular forum instead of the newbie forum.  

Thanks to everyone who made suggestions.

---

### Post by Luke on 2006-01-16
i doubt it will help, but you may want to try
```
ifdown wlan0
```
and then, as someone mentioned earlier,
```
ifup wlan0
```

---

