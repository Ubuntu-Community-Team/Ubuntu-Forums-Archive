---
title: "hardware ? linux support=Ubuntu support?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by RedDdog on 2008-02-25
I am brand new to Ubuntu (and Linux) and wanting to turn my old desktop into a home file server. I've looked around here and the forums are VERY helpful! 
QUESTION: If I see that a piece of hardware lists Linux under supported OS's am I good to use under Ubuntu?
This item is why I ask... but the answer will come in handy in the future as well
[PROMISE FastTrak TX2300 PCI SATA II 2-Port 3G/s RAID Adapter - Retail]("http://www.newegg.com/Product/Product.asp?Item=N82E16816102063")
I see hardware that says under OS's, "Linux:Red Hat, SuSE" I know this is so a newbie question but couldn't find a definitive answer.
I guess I'm hoping that Linux support means all flavors (but I have a bad feeling that may not be the case)

If anyone knows of a good PCI to SATA RAID card for my Ubuntu server lemmeknow 
:guitar: (I dont want to spend several hundred for a real hardware RAID controller)

---

### Post by sb12 on 2008-02-25
> **RedDdog said:**
> I am brand new to Ubuntu (and Linux) and wanting to turn my old desktop into a home file server. I've looked around here and the forums are VERY helpful! 
QUESTION: If I see that a piece of hardware lists Linux under supported OS's am I good to use under Ubuntu?
This item is why I ask... but the answer will come in handy in the future as well
[PROMISE FastTrak TX2300 PCI SATA II 2-Port 3G/s RAID Adapter - Retail]("http://www.newegg.com/Product/Product.asp?Item=N82E16816102063")
I see hardware that says under OS's, "Linux:Red Hat, SuSE" I know this is so a newbie question but couldn't find a definitive answer.
I guess I'm hoping that Linux support means all flavors (but I have a bad feeling that may not be the case)

If anyone knows of a good PCI to SATA RAID card for my Ubuntu server lemmeknow 
:guitar: (I dont want to spend several hundred for a real hardware RAID controller)

yes ubutnu is linux it will work

---

### Post by Cypher on 2008-02-25
You may want to do a little bit more research, fact that RedHat and SuSE are listed on Newegg doesn't mean a whole lot unless Promise themselves say so. Additionally, the line "Linux partial open source code" means that there are some binary components that might be best suited to work on Redhat or SuSE.

You might get a definitve answer if you go to Promise's website and explore, or better yet ask them directly about Ubuntu support..

---

### Post by RedDdog on 2008-02-25
Thanks both of you :-) Redhat and SuSE are also listed on the Promise corp site... This SATA card put the question in my head, The basis of my question is in general... if a piece of hardware states Red Hat and/or SuSE, or simply states Linux should it be good to go with Ubuntu? Seems like the answer is yes...

---

### Post by ByteJuggler on 2008-02-25
The answer is "maybe".  It depends on the particular hardware and whether the support is via open source freely available drivers or instead via their own propietary packaged drivers (typically then in a distribution specific package) or a combination of the 2.  Generally if the suport is open source based, then you won't have much problem using the device under any flavour of Linux as the drivers will likely be part of the kernel already (and thus be part of most distributions by default.)  However if the driver is proprietary then sometimes you will have problems using it on alternative distributions, chiefly in terms of fistly the exact kernel version in use on your distro not matching the version the drivers was built against, and other than that general issues with respect to installing the drivers, although those can usually be worked around with some effort.  

As for Promise controllers, I'm pretty sure that the Promise chipset is supported by Linux by default, but it's possible that Promise's own drivers provide extra functionality.  (I say this because I've got a motherboard with a similar chipset on which works fine with Linux.)

---

### Post by Cypher on 2008-02-25
The support for hardware in Linux is and the response to your question is really two-fold. If a piece of hardware has community support (in the Kernel or open source drivers), then you can get it working on _any_ Linux regardless of distrobution.

On the other hand, if the hardware has a driver that is released by the manufacturer, and if they do so in source format, then you can use any Linux distro, but if they release it in a binary format, then getting it to work on any Linux distro is possible as long as you keep the Kernel versions similar.

A lot of companies used RedHat as the Linux standard Distro as it was very prevelant (Ubuntu is now what Redhat used to be) and in turn they created drivers for specific version of Redhat's Kernels and gauranteed that the hardware would work with whatever scripts were needed.

So just seeing Linux as a supported OS, unfortunately, doesn't automatically mean that it will work on any distro..

---

### Post by ByteJuggler on 2008-02-25
[This thread]("http://www.linuxquestions.org/hcl/showproduct.php?product=3253&cat=all") seems to confirm my suspicion that this card should be supported by default.

---

