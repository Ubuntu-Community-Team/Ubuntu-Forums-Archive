---
title: "Wireless Problems...continued"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by devosion on 2007-09-29
I've been at this for several days now and I think i've finally isolated the problem. I managed to get Ubuntu to recognize my wireless linksys router and installed a windows driver through ndiswrapper to get it working. The first time I did this it connected to the network, or at least it acted as if it did. The network icon changed from the computers to the connection bar. I attempted an internet connection but that failed. Later I tried to ping my host but that didnt go through at all, all 4 packets failed. I pinged my localhost and that went through ok, so im beginning to think it has something to do with dhcp. Im very close guys and I really would appreciate any and all help I can get. By the way here are some general questions I need answered that would definately assist me.

Is there a way to manually feed a gateway into my connection settings?

Would it help if I fed my modem my routers mac address for easier connection? Never had to do this before but thought about it.

Oh and I am not getting an assigned IP from my modem either, its working on a basic level, but getting the network connection up is the problem.

---

### Post by kvelandia on 2007-09-29
i just posted something similar, but unfortunately i did not quite understand your approach to finding a solution.

my connection works just fine with windows.. (yuck) but i can not solve anything with the wireless connection issues on ubuntu
are u using feisty?

---

### Post by devosion on 2007-09-29
Yeah im using feisty too, and my connection works just dandy in windows too. 

Im going to attempt to see if the mac address for my router shows up in my modem after waiting a bit longer for replies to my threads. Im thinking if I can at least resolve that my modem is seeing my router that there is a solution to be had...

---

### Post by devosion on 2007-09-29
I just managed to get my connection up and running but suffice it to say im just a bit confused as to what I did to get it running. 

All I did was uncheck wired connection in the system > admin > networking settings and my connection immediately began working. Does this mean that my dhcp was being shared with a wired connection device that I did not have operating? Im not even sure what else I should ask but clarification on this would be nice if possible.

---

### Post by NHaGa on 2007-10-01
I have a similar problem in Feisty. My wireless connection works fine but every once in a while it drops. I figured out that if I go in system > admin > networking settings and uncheck and check the wireless connection it works again.

I'm new to linux so I don't really know where to look for the cause. I also notice that the drops are more frequent when I'm using Torrent or emule... 

Any thoughts?

---

### Post by devosion on 2007-10-01
Are you using a wusb54gv4? If you are then you will have to do what I do, that is disconnect the usb before booting ubuntu and once its completely loaded putting it back in. It'll work seemlessly for me then and it seems to be a bug exclusive to this linksys device. Give this a shot even if you dont have the same device.

---

### Post by NHaGa on 2007-10-01
Yes, that's what i'm using. I'll give it a try this evening and let you know... thanks

---

