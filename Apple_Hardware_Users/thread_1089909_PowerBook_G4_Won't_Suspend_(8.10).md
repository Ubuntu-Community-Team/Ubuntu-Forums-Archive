---
title: "PowerBook G4 Won't Suspend (8.10)"
date: 2009-03-07
forum: Apple Hardware Users
---

### Post by michaelrkn on 2009-03-07
I just installed 8.10 on my PowerBook G4. When I try to suspend, the screen flashes and sometimes has weird colors that kind of morph before coming back alive with a locked screen. When I unlock the screen, the wireless network has to reconnect, so something must be turning off. 

Here's the output of lspci:

0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0001:10:13.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:24:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:24:0d.0 Class ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:24:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:24:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)


Also, in case it's relevant, I have to use video=ofonly to boot. Thanks for any suggestions!
Michael

---

### Post by ant2ne on 2009-04-10
I'm having similar problems on my G4 PowerBook with debian xfce. I'm wondering if you had any better luck.

I was actually thinking of putting ubuntu on it if I could get better support.  My requirements would be...  Wifi with WPA1, Suspend and Resume from RAM or Disk (at least one of them), and Samba and tsclient. 

My research has led me to believe that the suspend/resume functions have been disabled for these notebooks due to a problem with the nvidia card and its closed proprietary drivers. But that info was pretty old.

---

### Post by gwydionwaters on 2009-09-25
bump
i too have this problem, suspend wakes immediately to a locked screen and wifi must reconnect.

---

