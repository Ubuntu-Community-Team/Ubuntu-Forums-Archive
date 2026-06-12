---
title: "How do I choose my wifi driver"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-10-02
I've installed Ubuntu 7.10 beta to check it out and report bugs to help out where I can. But I have a Belkin wireless G network adapter and before I installed 7.10 I used RT73 drivers for my wireless asapter But 7.10 had drivers that worked with it already. But there slower alot slower so I installed the RT73 driver thats faster but how do I start using it.

---

### Post by microsoft92sucks on 2007-10-02
Just how do I change the driver running this wireless adepter.

---

### Post by anewguy on 2007-10-02
I would assume that since there is a built-in driver, you will first need to add it to the /etc/modprobe.d/blacklist file, then use ndiswrapper for the other driver.:)

---

### Post by shad0w_walker on 2007-10-02
You would probably need to blacklist your current drivers (As pointed out by anewguy) and then you should install the drivers in the same way you did on your old install.

---

### Post by microsoft92sucks on 2007-10-02
Can someone tell me how I find the driver that I need to black list.

---

### Post by shad0w_walker on 2007-10-03
try opening up a terminal and running the command 

```
dmesg
```

That should list the wifi card and what driver it was started with. Dmesg puts out alot of info so you might want to also try this

```
dmesg | grep ralink
```

Hopefully that should filter out most of the unrelated information.

---

### Post by Austin_KW on 2007-10-03
the command lsmod will list the loaded modules/drivers
```
lsmod | grep usbcore
```
will tell you what drivers are using the usb


The driver you want to blacklist is rt73usb
You may also want to blacklist rt2500usb as it sometimes loads for the belkin.

Also you will want to remove the drivers from the current running system (as well as blacklisting them from loading again). To remove them
```
 sudo modprobe -rv rt73usb rt2500usb 
```

---

### Post by microsoft92sucks on 2007-10-03
What drivers should I blacklist.
```
spaje@EggHead:/usr/src/rt73-cvs-2007082915/Module$ lsmod | grep usbcoreusbcore               138248  6 usb_storage,libusual,zd1211rw,usbhid,uhci_hcd

```

And thanks for all the help so far.

---

### Post by Austin_KW on 2007-10-04
You do not have rt73 loaded. (Or the newer rt73usb)
You do have **zd1211rw** loaded. Is this a v4000 belkin usb adapter?

---

### Post by microsoft92sucks on 2007-10-04
> **Austin_KW said:**
> You do not have rt73 loaded. (Or the newer rt73usb)
You do have **zd1211rw** loaded. Is this a v4000 belkin usb adapter?
I'm not sure if it's a v4000 or not but this is the one I have.
[http://catalog.belkin.com/IWCatProductPage.process?Product_Id=179211](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=179211)
And I haven't installed the rt73 drivers yet. But heres a link to the how to that I use to install them. It black list some drivers too. I wanted to know what I was doing before I installed it.
[http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73)

---

### Post by Austin_KW on 2007-10-04
There are a number of different chipsets for this adapter. You can open the adapter by splitting it along the seam using a fingernail. Read the chip ID.

---

