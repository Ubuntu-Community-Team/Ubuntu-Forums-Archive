---
title: "wusb11"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by valinator7 on 2007-12-12
Hi,  I jsut installed unbunta 7.10.  I then pluged in my wusb11 network adapter.  I tryed the driver disk,  it didn't work of cours cuz it's for xp.  then I nosed around  systems>network and didn't see anything interesting (not sure what i was looking for).  anyway, any suggestions on where to find a driver or how to get started.

---

### Post by louieb on 2007-12-12
[FONT=Arial][SIZE=2]Oh lucky you. Did a [Google Linux Search]("http://www.google.com/linux")  on wusb11. 
Found a Linux driver at [http://www.opendrivers.com/driver/214899/linksys-wusb11-instant-wireless-usb-network-adapter-v2.5-driver-linux-free-download.html](http://www.opendrivers.com/driver/214899/linksys-wusb11-instant-wireless-usb-network-adapter-v2.5-driver-linux-free-download.html)
Also found a discussion on using ndswraper on the Knoppix forum
[http://www.knoppix.net/forum/viewtopic.php?p=115768](http://www.knoppix.net/forum/viewtopic.php?p=115768) Knoppix like Ubuntu is Debian based.  
and a discussion about it  on linuxquestions.org [http://www.linuxquestions.org/hcl/showproduct.php?product=71](http://www.linuxquestions.org/hcl/showproduct.php?product=71)
Apparenty some distros like Mandriva have the driver. Kind of supprised Ubuntu doesn't. Try booting with it plugged in and see if it get picked up then.

in a terminal window run 
[/SIZE][/FONT]```
ifconfig
```
and see if you have an entry for wlan0 or something similar. 
Don't have that adaptor but maybe this will get you start in the right direction. 
[FONT=Arial][/FONT]

---

### Post by valinator7 on 2007-12-12
Thankyou, thankyou- that will keep me bussy for a while

---

### Post by timcredible on 2007-12-29
even luckier for us (i just bought a wusb11 also) is that the linux-wlan-ng driver is in synaptic, so just install the package from synaptic.  i won't be able to test this until monday however, so if i remember, i'll post what happens with it then

---

### Post by wieman01 on 2007-12-29
> **timcredible said:**
> even luckier for us (i just bought a wusb11 also) is that the linux-wlan-ng driver is in synaptic, so just install the package from synaptic.  i won't be able to test this until monday however, so if i remember, i'll post what happens with it then
Does it support WPA or WPA2 by chance? Any idea? Would be cool to know.

---

