---
title: "ndiswrapper, hwu54g, edy, complete noob"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by metalucard on 2007-03-28
Hi,
I am a complete noob to the linux logic, so please bare with me. 
so I installed ubuntu on my desktop, and everything is fine except the internet.
after a huge adventure, I came to discover the deb packages, and how to install network manager. also I use a HWU54G USB-Wireless Adapter (rev2), which is recognized by default in edgy, problem is I think the driver is incompatible with the wpa_supplicant thing, so I get no choices for wpa in network manger.

So, I came to understand that the best solution would be to install ndiswrapper, which supposedly works with wpa_supplicant, and uses the windows driver. 

Now all I know is that I might need to install the deb package, which I found in this link:
[http://packages.ubuntu.com/edgy/misc/ndiswrapper-utils-1.8](http://packages.ubuntu.com/edgy/misc/ndiswrapper-utils-1.8)

from here on I have no Idea what to do, as I said I am a complete noob to this, I am using my fathers laptop which runs WinXP, so I can download the required files for my desktop (which has edgy), all I need to have for a successful linux conversion is the internet.
I would appreciate any help in this problem, 
thank you very much.

---

### Post by digital_sabotage on 2007-03-28
i'm a near noob but here's how i got my wireless going...

installed ndiswrapper by way of >System>Administration>Synaptic Package Manager 

...after install was complete i went to >System>Administration>Windows Wireless Drivers and selected "install new driver"  ...from there you just browse to the folder that contains your windows ".inf" file

...after that you should see your wireless connection and status in >System>Administration>Networking

...hope this helps:-)

---

### Post by shirilover on 2007-03-28
You shouldn't need ndiswrapper to get your HWU54G dongle working. I have such a device and followed this guide -> [How TO - Zydas ZD1211 on Edgy with WPA]("http://http://www.ubuntuforums.org/showthread.php?t=288753")

---

