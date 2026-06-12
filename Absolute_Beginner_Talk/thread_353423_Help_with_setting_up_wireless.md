---
title: "Help with setting up wireless"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Smiley-Dude on 2007-02-04
Ok, so I am using an Hp DV2000 laptop, with a Broadcom wireless card.  

When I ran the lspci command I got this message:

```
Network Controller: Broadcom Corporation Unknown Device 4311 (rev 01) 
```

Earlier yesterday I ran iwconfig and ifconfig to find out where my card was running from, which turned out to be eth1, so I installed ndiswrapper and the bcmwl5sys.inf driver.  When I installed the driver it saidd that there was no hardware for the driver installed.  

Today when I logged into my comp, I repeated the iwconfig and instead of 4 different sections (lo, eth0, eth1, and sit0) only lo, eth0, and sit0 appear.  When I input ifconfig the only thing that appeared was the lo information.  

I read the tuts on how to get the Broadcom Wireless cards working but none of those things worked.  

I am confused as to what I should do, what I should have done, and what I should not have done.  

Any help is greatly appreciated.

---

### Post by Bachstelze on 2007-02-04
First, you need to disable the bcm43xx driver if it is not working.

Second, you need to make sure you installed the correct INF for your card. The 'hardware missing" message usually means you installed a wrong one.

---

### Post by Smiley-Dude on 2007-02-04
I disabled the bcmxx driver, and I know that that is the correct driver because I downloaded it from the HP website.

---

### Post by Bachstelze on 2007-02-04
What annoys me here is that you ran *iwconfig* and saw your wireless interface as eth1, meaning there already was a driver for it running. So maybe the existing driver somehow made your ndiswrapper installation fail. Try removing the driver in ndiswapper and installing it again. You can use *ndiswrapper -l* to make sure it has been properly installed. If you see "driver installed, hardware present", all you have to do then is *sudo depmod -a && sudo modprobe ndiwsrapper* and you should have your wireless interface in *iwconfig*.

---

### Post by Smiley-Dude on 2007-02-04
It says that the driver is installed, but it doesn't say anything about the hardware.  When I tried running the command but it just went to a new line, without doing anything.  

I have also noticed that my computer doesn't seem to think eth1 exists anymore.  I have it set as my network but when I click on the Network Connection thing in the upper right corner it says SIOCGIFFLAGS error: No such device

---

