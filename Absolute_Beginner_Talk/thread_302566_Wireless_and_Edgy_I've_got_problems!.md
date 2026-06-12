---
title: "Wireless and Edgy: I've got problems!"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by unbuntu kid on 2006-11-18
After recently upgrading to Edgy, I tryed to configure my wireless.  As you may guess, it was total disaster.  
Wifi-Radar can decect networks, but when wifi-radar runs, it kills the mouse driver and the mouse icon gets high and starts zooming all around my screen whenever I touch my touchpad.  
The network icon in the upper right hand will not let me select wlan0 from the dropdown list, although in the networking area, wlan0 is already configured, although the ubuntu networking system cannot decect networks.  
The blue wifi light (the only thing that seems to work:)) is on and I am praying.

Thank you in advance!

---

### Post by MrFSL on 2006-11-18
Unfortunately configuring wireless in Ubuntu still is lacking a bit. - I tried wifi radar and wasn't impressed.

My suggestion is to use iwlist and iwconfig in conjunction with hand editing the /etc/network/interfaces config file to set it up the way you want. Once all is configured correctly restart networking and you should be good to go.

---

