---
title: "No internet after installation!"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by peterkeyani on 2008-03-16
Hi,

Just installed ubuntu 7.10 on a old Intel Pentium 4 1.5GB 256MB NEC Powermate.

Plugged in the ethernet and no internet!

Any ideas?

Thanks

Peter

---

### Post by handydan918 on 2008-03-16
Open a terminal and do ```
sudo dhclient
```

If that doesn't work, post the output of ```
lspci | grep -i net
```

---

### Post by ugm6hr on 2008-03-16
The following will confirm the ethernet installation:

```
lspci
lshw -C network
route
```

If that checks out OK (post the output here if you don't know what you are looking for), then this may be the problem:
[http://ubuntuforums.org/showpost.php?p=4522099&postcount=2](http://ubuntuforums.org/showpost.php?p=4522099&postcount=2)

---

### Post by peterkeyani on 2008-03-16
> **handydan918 said:**
> Open a terminal and do ```
sudo dhclient
```

If that doesn't work, post the output of ```
lspci | grep -i net
```


Thanks for your reply.

I tried the first step and it didnt work.

The second step was a bit confusing because I didnt reconise the vertical line symbol.
So I typed in just lspci
It returned a lot of lines of information about system hardware. I couldnt cut and paste in this reply since that machine has no internet connection obviously.
The first line was
00:00.0 Host bridge: Intel Corporation 82845 - 845 {Brookdale} chipset Host bridge (rev 03)
There was a line about the ethernet which I assume is the most relevent
02:00 Ethernet controller: Accton Technology Corporation SMC2 - 1211TX (rev10)

I assume the problem is that ubuntu does not reconise the ethernet board? Will it need a new ethernet board for this pc to be used as a internet terminal? Will "Hardy" be able to reconise it?

Thanks for your help.
Pete

---

### Post by dptxp on 2008-03-16
Try sidux. If it does then there is a chance that Hardy will. Just a chance.
Or maybe you can use ndiswrapper. sidux comes with it. You can install
in Ubuntu too.

---

### Post by peterkeyani on 2008-03-16
> **dptxp said:**
> Try sidux. If it does then there is a chance that Hardy will. Just a chance.
Or maybe you can use ndiswrapper. sidux comes with it. You can install
in Ubuntu too.

Is replacing the ethernet board with a more modern one a good idea?

thanks
pete

---

### Post by dptxp on 2008-03-16
sorry, thought you had new hardware. I have never used ndiswrapper but that makes use of Window$ drivers. If you got Window$ driver for it (the ,inf file) and it works with Window$, you can try with advice from forums here.
Wait for more replies, from those who know better.

---

### Post by handydan918 on 2008-03-16
> **peterkeyani said:**
> Is replacing the ethernet board with a more modern one a good idea?

thanks
pete

Heh. A more ancient one is more likely to yield success than a newer one...
If this is a driver issue, anything that's has been on the market for several years is more likely to have drivers than something newer.

---

### Post by lswest on 2008-03-16
can you post the output of ```
sudo ifconfig
``` and ```
sudo ifdown eth0
sudo ifup eth0
sudo dhclient eth0
``` otherwise, try installing Ubuntu with the cable plugged in, i find sometimes it doesn't recognize the card when installing if it's not active.

also > 02:00 Ethernet controller: Accton Technology Corporation SMC2 - 1211TX (rev10) means that the card IS recognized, since it's listed under the PCI devices.

---

### Post by jdgiotta on 2008-03-16
> **lswest said:**
> can you post the output of ```
sudo ifconfig
``` and ```
sudo ifdown eth0
sudo ifup eth0
sudo dhclient eth0
``` otherwise, try installing Ubuntu with the cable plugged in, i find sometimes it doesn't recognize the card when installing if it's not active.

also  means that the card IS recognized, since it's listed under the PCI devices.

As a tip to posting terminal output, if you have a thumb drive (or even a digital camera or mp3 player, most can used as such) then save the output to text file so you can retrieve it again for your reply. It maybe trouble some, but I'm sure your problem can be solved.

---

### Post by ugm6hr on 2008-03-16
> **jdgiotta said:**
> As a tip to posting terminal output, if you have a thumb drive (or even a digital camera or mp3 player, most can used as such) then save the output to text file so you can retrieve it again for your reply. It maybe trouble some, but I'm sure your problem can be solved.

This is a good idea.  Copy & Paste to USB flash disk.

You should not need a new ethernet card.

As I posted above, *lshw -C network* will tell you if your ethernet card has an appropriate driver (it will say driver=xxxx).

*ifconfig* should confirm an IP (e.g. inet addr:192.168.1.5) if connected.

*route* will confirm the same.

---

### Post by Darganot on 2008-03-16
A GUI solution:

In the menus at the top of the screen go to:

System --> Administration --> Network 

Enter your password and you should see all the devices connected.  You can set up your DNS and ip's from here if you're running a static ip.  If not or you don't know select DHCP or some kind of dynamic or automatic ip.  Wireless devices should also be listed here but I don't know quite as much about configuring those.  Make sure you check the box next to the device you want to use and close the window.  The changes should take effect, but you might need to reboot.

---

