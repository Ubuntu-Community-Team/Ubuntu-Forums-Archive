---
title: "Ndiswrapper help wanted"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by SuperCool4678 on 2007-04-28
In another post, someone suggesting installing ndiswrapper to fix my problem connecting to wireless networks on my laptop.  I installed it, and I installed the driver for the D-link adaptor I use, but I don't understand what I'm supposed to do now.  I followed these instructions:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

but I got lost somewhere in the "Configure interface" section at the bottom.  What do I do with ndiswrapper now that I have it installed?

---

### Post by Bachstelze on 2007-04-28
Type

```
sudo iwconfig
```

and paste what you get.

---

### Post by SuperCool4678 on 2007-04-28
lo        no wireless extensions


eth0      no wireless extensions


rausb0    RT2500USB WLAN  ESSID:"homenet"  Nickname:""
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:46:AB:7E:CE
          Bit Rate=54 Mb/s
          RTS thr: off   Fragment thr: off
          Encryption key: off
          Link Quality=72/100  Signal level:-60 dBm  Noise level:-204 dBm
          Rx invalid nwid0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries: 0  Invalid misc:0   Missed beacon:0

---

### Post by Bachstelze on 2007-04-28
Drivers are not installed properly, then. Whad kind of WiFi adapter do you have (PCI, USB...) ?

---

### Post by SuperCool4678 on 2007-04-28
I didn't have the adaptor plugged in when I typed "sudo iwconfig" the first time.  I added the additional info above.

---

### Post by Bachstelze on 2007-04-28
Then you can configure your interface normally, either from command line with *iwconfig* or with whatever GUI-thingie Ubuntu provides for it.

---

### Post by SuperCool4678 on 2007-04-28
I still have no idea what to do.  When I was using Dapper on this laptop before, I didin't have to configure anything; I was able to just plug the adaptor in and connect.  How do I set up Feisty to be able to do that?

---

