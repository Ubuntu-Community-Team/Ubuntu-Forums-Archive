---
title: "Some web sites load, others don't"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by stevelasvegas on 2008-02-01
I've read all similar posts but none apply so here's my situation.
Using either Firefox or Opera the results are the same.
Using wireless connection some web sites will not load, other will.
Using wired connection everything is fine.
That's the basics; suggestions appreciated.

---

### Post by jan quark on 2008-02-01
what are your network devices?

are there some similarities between the websites that do  not load?

like many videos? many java applications? some other similarities?

---

### Post by stevelasvegas on 2008-02-01
>          what are your network devices?I don't know how to tell

>  are there some similarities between the websites that do  not load?Not that I can determine. For example, I can go to just about anywhere Google and everything loads. If I go to usatoday.com, no part of the page will load. When I go to cox.com, the main page loads but stalls when the main page is calling to bring something in from somewhere else. It is perplexing. I have read about IPV6 and that doesn't fix it. The part of this that makes no sense to me is that I can go to some pages and not others. I thought I either have a connection or not, apparently not the case. If I connect an either net cable to the laptop, it displays all pages I go to just fine.

>  like many videos? many java applications? some other similarities?
Doesn't seems to be associated with any of the above. I can see java enabled apps and videos at the sites I can load.

---

### Post by jan quark on 2008-02-01
hey that's weird

to tell what your network devices is run the following in the terminal and post the result here

```
lspci
```

and you say that everything is displayed correctly when you are online with the net cable..
never heard of something like that will aks some geeks

---

### Post by stevelasvegas on 2008-02-01
```
steven@ubuntu:~$ lspci
```00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

---

### Post by jan quark on 2008-02-01
after a discussion with some friends
here is what  might affect your network

switch to the net cable connection and go to system > administration > network

click on the DNS panel and post the Ip address here 

than switch to the wireless connection and do the same

is there any difference between the two DNS settings ?

---

### Post by stevelasvegas on 2008-02-01
Wireless - DNS = 192.168.15.1 (my default gateway)
Wired - DNS = 192.168.15.1
They are the same.
I did try using the 2 DNS server addresses at opendns.org with the same results.

---

### Post by stevelasvegas on 2008-02-01
I figured I would try to isolate the problem. It is either something on my laptop computer or something with my network. I dual boot with this computer, WinXP and Ubuntu. I can connect to all sites with my wireless connection in Windows; the problem is in Ubuntu. I restored my Ubuntu to an earlier time (thanks to a WUBI install, that was easy) and had the same issues.
I wanted to see if other wireless users (using other computers) would have the same problem, trying to see if it was my network, but no others around and they probably aren't using Ubuntu. And that didn't seem like the right way to go because I was able to connect just fine wireless with XP. I was going to try my laptop with a different wireless connection but my neighborhood all encrypt their routers, none open.
So I started looking at my network. I reset my wireless router; no help. While I was messing with the wireless router, I found a recent firmware update and I installed it. Now everything is working fine. I really don't know why (which is the part that aggravates me), but the bottom line, it is working!
If anyone else is having this sort of problem, maybe this exercise will be helpful to them.
Thanks for your help.

---

