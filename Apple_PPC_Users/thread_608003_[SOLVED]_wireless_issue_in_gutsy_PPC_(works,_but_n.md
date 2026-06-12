---
title: "[SOLVED] wireless issue in gutsy PPC (works, but no list of availlable networks)"
date: 2007-11-09
forum: Apple PPC Users
---

### Post by wickstopher on 2007-11-09
Hello!  I finally got around to doing a clean install of Gutsy on my G4 Titanium PowerBook.  It took a couple of tries, but I finally got it with the Alternate Install disc.  I've pretty much got everything to work (had to install an older kernel to get sound), and I'm enjoying it.  One thing that doesn't work that worked just fine out of the box with Feisty (also works in my x86 install of Kubuntu Gutsy) is wireless.  I can connect to my home wireless network.  It is the network that I entered manually for use during the installation process, and it automatically connects to that network when I boot up the system.  The problem is that I can't connect to any other wireless networks.  I just don't have the option.    There is no list of networks that pops up when I right-click (i.e.F12) the knetworkmanager applet.  When I click on the applet (or "show connection information") it says "no active devices" even though I am most definitely (at the time of this typing) connected to my home wireless network.  I'd like to be able to connect at wifi spots or to networks at friends' houses.  Anybody got a solution here?  I feel like I'm probably missing something stupid, but this worked out of the box in Feisty PPC.  Thanks!

---

### Post by smackswell on 2007-11-12
I'm pretty sure I have the same PB as you, and I couldn't get a list or different available networks in Feisty. 

Try Wifi-radar:

[http://www.linux.com/articles/55647](http://www.linux.com/articles/55647)

Works very well for me. Btw, how hot is your laptop getting with gutsy? I tried it for long enough to love it and realize my compy was way too hot.  Any ideas on a fix? I want Pidgin back.:(

---

### Post by wickstopher on 2007-11-12
I'll give that a shot and let you know what happens.  My laptop gets fairly hot in general (with gutsy or with os x).  Maybe a bit hotter in gutsy, but it's hard to say.

---

### Post by wickstopher on 2007-11-13
Well, I installed wifi-radar via apt-get, and still no dice.  The program won't even start up.  Not sure if I'm doing something wrong here.  I select the program from the menu, and nothing happens.

---

### Post by pxwpxw on 2007-11-13
> **wickstopher said:**
> Well, I installed wifi-radar via apt-get, and still no dice.  The program won't even start up.  Not sure if I'm doing something wrong here.  I select the program from the menu, and nothing happens.
You could try restart with wireless router on.
Then with whatever networking is in fact running post the results from:

```

ifconfig
sudo iwconfig
sudo iwlist scan
cat /etc/network/interfaces
lshw -class network

```

Should help to find an answer.

---

### Post by wickstopher on 2007-11-13
Here is the requested command output.  I edited the SSID and WEP keys that were output, but I'm assuming that won't make a difference in diagnosis.


```

wickstopher@cecilap:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:95:75:D6:96
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:41 Base address:0x1400

eth1      Link encap:Ethernet  HWaddr 00:30:65:29:93:77
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:65ff:fe29:9377/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18751 errors:3 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:44884093 (42.8 MB)  TX bytes:2662660 (2.5 MB)
          Interrupt:57

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```

wickstopher@cecilap:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"MyNetwork"  Nickname:"Nickname?!?"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:CE:8A:39:5A
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:MyWepKey   Security mode:open
          Power Management:off
          Link Quality=55/92  Signal level=-41 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:7
          Tx excessive retries:3  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

```

wickstopher@cecilap:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:A3:19:B6:05
                    ESSID:"Morris' Network"
                    Mode:Master
                    Frequency=2.437 GHz (Channel 6)
                    Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on

sit0      Interface doesn't support scanning.

```

iwlist scan is showing another network in my neighborhood, "Morris' Network" (I do not broadcast my SSID)

```

wickstopher@cecilap:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid MyNetwork
        wireless-key1 MyWEPKey


```

```

wickstopher@cecilap:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: UniNorth GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0002:24:0f.0
       logical name: eth0
       version: 01
       serial: 00:0a:95:75:d6:96
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=gem latency=16 maxlatency=64 mingnt=64 module=sungem multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:30:65:29:93:77
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.13 multicast=yes wireless=IEEE 802.11b


```


Hope this helps!  Thank you!

---

### Post by pxwpxw on 2007-11-14
> **wickstopher said:**
> Here is the requested command output.  I edited the SSID and WEP keys that were output, but I'm assuming that won't make a difference in diagnosis.


Hope this helps!  Thank you!

That all looks normal for a single wireless network, as you already stated, except that it does not show the wireless driver for some reason, I dont know if you have bcm43xx broadcom, but it is working, and that is not the problem. 

I tried wifi-radar here, but got nothing useful to report, and I dont have your system (I am using xubuntu710 on a powermacG5, with just one local wireless net visible), so cant really suggest how to configure your system for your needs.

I did find that wifi-radar had to be configured with ssid and wep key to connect initially by selecting "New" (See attached picture of wifi-radar)
It seems to need initial configuration for all the networks you want to use.

I manually configured /etc/network/interfaces, just for a test, dont know if this is a good idea, but it worked
```

$ cat /etc/network/interfaces 
# The loopback network interface
auto lo
iface lo inet loopback

#my Apple Broadcom card is eth0 here
#it normally has my wireless router ssid and wep key
#but this simple verision lets wifi-radar take charge.

iface eth0 inet dhcp
auto eth0

```

On ubuntu 704 feisty, the gnome network manager applet worked, and I think it had a roaming option.

 There is a bug with the ubuntu 710 gutsy powerpc nm-applet (network-manager-gnome package), I dont know if the kubuntu version is also bugged. I removed it, it was a nuisance.

I normally configure my single local wireless net,( WEP security key ), just using the basic ubuntu or xubuntu desktop network-admin application to change from wireless to wired occasionally, with a restart, no Nm-applet, not very convenient. 

Hopefully some wifi-radar or wicd  enthusiast can help you further, the info you posted should help.

---

### Post by kugn on 2007-11-15
I'm no expert in this, but it seems to me that your wireless has been set up to bypass knetworkmanager. IIRC (it was a long time ago) that happened to me when i messed with the /etc/network/interface and other config files, so that the wireless was connected through those config files rather than through networkmanager.
SInce u seemed to suggest you did quite a bit of manual configuration, did you mess with the network config files? If you did, you could try using the backup files or something.

---

### Post by wickstopher on 2007-11-15
I didn't really do much manual configuration for the network.  I only entered the SSID and WEP key when prompted during installation via the alternate install disk.

---

### Post by kugn on 2007-11-15
I suppose that could be enough to alter /etc/network/interfaces. Do check it. My copy only has two lines

auto lo
iface lo inet loopback

try commenting out the other lines and see if it works. knetworkmanager takes a while to refresh though. might have to restart the app and all. and restart /etc/init.d/networking and /etc/init.d/hal.

---

### Post by schnook9 on 2007-11-15
wow, that is incredible.  I've been having this same issue since I upgraded to gutsy on my dell d820, and commenting out the eth0 and eth1 lines in the interfaces file made the instant change to knetworkmanager.  I did it one at a time, and the other items in there (eth2, wlan0, etc) can all do their thing automagically as they please.
I guess knetworkmanager is saying that anything not auto configured in the interfaces file is allowed to be managed by it.... OR, there's some other moniker that should be put there to allow knwmgr  to utilize it. 

Either way, it works this way, and i'm happy as can be. much thanks!!

also, there's a related launchpad question I found related to this that seems to confirm this thinking as well.  enjoy!

[https://answers.launchpad.net/ubuntu/+source/knetworkmanager/+question/15308]("https://answers.launchpad.net/ubuntu/+source/knetworkmanager/+question/15308")

---

### Post by wickstopher on 2007-11-15
I'll be.  It worked for me, too.  Thanks very much!

---

### Post by locutus42 on 2008-02-10
Gutsy Kubuntu was giving me problems and after over an hour, I found this thread and fixed the problem by commenting out everything but the "lo" device in /etc/network/interfaces.

Network-manager should put a couple of commented lines in that file saying what the requirements are....

BTW, it also explained why the knetworkmanager was not showing my wired connection details previously. I HATE when these kinds of things happen.

---

