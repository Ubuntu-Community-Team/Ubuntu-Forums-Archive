---
title: "Wireless connection probs.."
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Ircha on 2007-02-24
Well, back again, I want to try and connect my Linux Ubuntu to the internet with a wireless network card, Canyon 802.11 Wireless network adapter, when i type iwconfig, this is what it says.
lo = no wireless extensions
eth0 = no wireless extensions
eth 1 =
802.11g zd1211 ESSID: ""
Mode: Managed Frequency:2.412 Access Point:Invalid. Bit Rate=1 MB/s signal 88/100........
sit0 = no wireless extensions

If I go to System/Administration/Networking, there are now 3 different alternatives
Wireless connection (the one i want to use)
Wired connection
Modem connection.

I clicked wireless connection, selected properties, and wrote in the ESSID, password type hex, and the password [i checked the password was correct] and pressed ok, it said "configuring interface" and after that it's done. But I still don't have any connection to the internet
what should I do?
Thanks,
Erik.

---

### Post by hyper_ch on 2007-02-24
In the screen where you have the three devices listed, can you select there a "default" one? On the bottom a little dropdown menu?

---

### Post by Ircha on 2007-02-24
> **sjau said:**
> In the screen where you have the three devices listed, can you select there a "default" one? On the bottom a little dropdown menu?


Nope, there's 4 tabs, a Connections, a General, a DNS, a Hosts, and there's a property button to the right, a location bar at the top, a close button in the bottom right, and a help button.

---

### Post by hyper_ch on 2007-02-24
on the connections screen, there is no dropdown on the bottom to select teh default network interface?

---

### Post by Ircha on 2007-02-24
> **sjau said:**
> on the connections screen, there is no dropdown on the bottom to select teh default network interface?


No, I just had a chat with a guy in IRC and he was "Officially stumped."
when I type Lspcsi there is no Marvel Libertas, I don't know why he asked that, but you maybe want to know that.

---

### Post by hyper_ch on 2007-02-24
Can you post to content of

/etc/network/interfaces ?

P.S.: Make sure not to post any wireless-key :)

---

### Post by Ircha on 2007-02-24
> **sjau said:**
> Can you post to content of

/etc/network/interfaces ?

P.S.: Make sure not to post any wireless-key :)

wasn't sure what you meant, but I entered the /etc/network/interfaces and inside it I saw auto eth1 iface eth1 inet dhcp, the wireless essid and key.

---

### Post by hyper_ch on 2007-02-24
please post what you see in that file :)

---

### Post by tgalati4 on 2007-02-24
What version of Ubuntu? If you are using Edgy, then you may have to blacklist to default driver that gets installed.


I am running ndiswrapper with a Marvel Libertas driver.  I couldn't get the open source driver to work so I had to resort to ndiswrapper.  Search the forums for ndiswrapper, there are lots of decent tutorials.

Try:

sudo ifconfig eth1 essid "My own private wireless network"
sudo ifconfig                  (to see if the essid sticks)

No quotes needed if your Access Point (AP) is a single word.  Use quotes if you have a multiple word AP.

---

### Post by Ircha on 2007-02-24
Btw, I just realised something, before I was using another wireless card, but since it didn't have any support on linux ubuntu I switched networks card with the other computer, but the previous network cards drivers had been wrapped with ndiswrapper and i had used the modprobe command, how can I erase previous modprobe data? will it work you think?

---

### Post by Ircha on 2007-02-24
> **tgalati4 said:**
> What version of Ubuntu? If you are using Edgy, then you may have to blacklist to default driver that gets installed.


I am running ndiswrapper with a Marvel Libertas driver.  I couldn't get the open source driver to work so I had to resort to ndiswrapper.  Search the forums for ndiswrapper, there are lots of decent tutorials.

Try:

sudo ifconfig eth1 essid "My own private wireless network"
sudo ifconfig                  (to see if the essid sticks)

No quotes needed if your Access Point (AP) is a single word.  Use quotes if you have a multiple word AP.

Using Ubuntu 6.10 Edgy Eft, and when i typed sudo ifconfig eth1 essid thornet it said
essid: Host name lookup failure
ifconfig: ´--help' gives usage information

How do I blacklist then?

---

### Post by linux_kid on 2007-02-24
Is your network essid correct, because it is coming up with no connection point?

And try to see if your neighbor's wifi essid's come up with the following command,```
sudo iwconfig eth1 scan
```

EDIT: The latter seems to only work in Dapper.

---

### Post by Ircha on 2007-02-24
> **linux_kid said:**
> Is your network essid correct, because it is coming up with no connection point?

And try to see if your neighbor's wifi essid's come up with the following command,```
sudo iwconfig eth1 scan
```

EDIT: The latter seems to only work in Dapper.

I wrote sudo iwconfig eth1, scan didn't work, anyways, this is what showed.

--
eth1  802.11g zd1211 ESSID: " "
        Mode:Managed Frequency:2.412 GHz Acess Point: Invalid
        Bit rate: 1MB/s
        Encryption key:the correct key, in caps though?
        Link quality=71/100 Signal level=86/100
        Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
        Tx excessive retries0 Invalid misc:0 Missed beacon:0
'

For some reason the ESSID = " ", not Thornet, as I specified it, how can I change that?
--

---

### Post by handaxe on 2007-02-24
Assuming that you have driver & other hardware issues sorted out, you might try WICD as your manager of wireless connections. Under active development.

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

Deb install. Also installs a tray icon BUT does not put an entry is startup.

Do that by going to "System" "Preferences" "Sessions"  "Startup   Programs" and enter /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper (Doh!)).

WICD handles many forms of encryption and unlike Network Manager does not require you to mess about with /etc/network/interfaces.

Wicd has its own forum (details in link above). Use that if you will.

HA

---

### Post by linux_kid on 2007-02-24
> For some reason the ESSID = " ", not Thornet, as I specified it, how can I change that?
To change the default essid,  go to System->Administration->Networking and click on your wireless interface.  Type in all of the correct info and try again.

---

