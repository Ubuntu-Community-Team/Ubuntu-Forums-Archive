---
title: "[INTEL] 8.04 Wireless on 2ndgen Macbook"
date: 2008-04-27
forum: Apple Hardware Users
---

### Post by Hatfield on 2008-04-27
Having trouble with wireless after installing 8.04 64bit on my MacBook.
My stats:
Model Identifier: MacBook2,1
Processor Name: Intel Core 2 Duo
Processor Speed: 2.16 GHz
Number Of Processors: 1
Total Number Of Cores: 2
L2 Cache (per processor): 4 MB
Memory: 2 GB

Installed the MadWifi drivers per:
[https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688](https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688)

My wireless started working and could see my network and connect.  Works for the first 2 or 3 websites and then stops working.

I went into the terminal and ran
```
cat /etc/network/interfaces
```
got
```
auto lo
iface lo inet loopback

```

Ran
```
sudo gedit /etc/network/interfaces
```
and edited to
```

auto lo
iface lo inet loopback

#iface eth0 inet dhcp
#address 192.168.0.130
#netmask 255.255.255.0

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp


#iface ath0 inet dhcp
#wireless-key ############
#wireless-essid Gallipoli

auto wlan0
#iface wlan0 inet dhcp

#auto eth0
```

And still the same thing.  My wireless only works for a very short time then stops.  Still "connected" but FireFox comes up with an error.

Any suggestions?

---

### Post by Rog-Mahal on 2008-04-27
If you're using the madwifi drivers, ath0 is the thing you want uncommented. I think you also want the iface entry uncommented as well. You have a lot of interfaces there, where did they come from? Did you install drivers via madwifi and ndiswrapper? because that would cause problems.

---

### Post by Hatfield on 2008-04-27
Alright.  I am a relative newb, but I think I understand what you're saying.

I had received help a while ago and was told to go in and gedit some stuff.  It worked for a while, but then stopped.  I only assumed I had to do it again.  From what you're saying, it sounds like I shouldn't have.  So I'll backtrack.

I went back into gedit and unedited what I had added so
```
cat /etc/network/interfaces
```
now again reads
```

auto lo
iface lo inet loopback
```

Same thing.  It works for the first few sites and then it stalls.
Ex: "Looking up www.bbc.co.uk"
.......
"Address Not Found"


And I am quite the newb.  Still learning.

---

### Post by Rog-Mahal on 2008-04-27
Could you give the output of the command "ifconfig"? Maybe that will give some more information to start from. Hmm, so you do get wireless functionality for a little while?

---

### Post by yousufinternet on 2008-04-27
i used ndiswrapper to install the driver 
and it worked immediatly -after a restart of course- without any problems 
and all was done by GUI
try to burn windows drivers cd 
and install the driver from their using ndiswrapper and unrar

---

### Post by Hatfield on 2008-04-27
> **Rog-Mahal said:**
> Could you give the output of the command "ifconfig"? Maybe that will give some more information to start from. Hmm, so you do get wireless functionality for a little while?

```

hatfield@Macbook:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1b:63:c8:51:e3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3976 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2548 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2544251 (2.4 MB)  TX bytes:410380 (400.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:19:e3:40:32:a8  
          inet addr:192.168.0.138  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:e3ff:fe40:32a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13003 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7419906 (7.0 MB)  TX bytes:1780222 (1.6 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99641 (97.3 KB)  TX bytes:99641 (97.3 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1B-63-C8-51-E3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127882 errors:0 dropped:0 overruns:0 frame:2628
          TX packets:10548 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:12658637 (12.0 MB)  TX bytes:845881 (826.0 KB)
          Interrupt:17 

hatfield@Macbook:~$ 

```

It gets even weirder.  I just unplugged the ethernet connection to take the MacBook into the other room to show off Ubuntu to a friend.
Did the same thing as usual: connected to my network and worked for a few sites before failing.  I left Firefox alone for about 10 minutes and showed off some other stuff before trying Firefox again.  Did the same thing as before.  Worked for a little bit then stopped again.  So wireless is just sporadically working.  Weird.


Yousuf, that is a possibility.  If I can't get MadWifi to work, ndiswrapper it is.

---

### Post by Hatfield on 2008-04-28
Anyone wanna take a stab?  I'm at a loss right now.  Wireless works for a almost 45 seconds at first before stopping.

---

### Post by brambles on 2008-04-28
Ah Ha! Somebody with exactly my problem! Connects to network briefly then dies. I've tried using wicd instead of network manager in case it was that-same deal. Thought it might be because of wpasupplicant but it hasn't changed for a while and have narrowed it down to losing dns after an initial 'hit' when connecting (try using dig when it fails and I bet you've lost connection to the nameserver).

C2D 2 gig here. This started about a week before release tho' not sure what brought it on.

Painful but glad I'm not the only one

Cheers

Hardy 64 bit with madwifi svn updated today

---

### Post by brambles on 2008-04-28
Well,  Having had a mature think over my last post I went back to basics and rather than blaming Hardy went back to the root of the problem ie the driver and recompiled an old nightly snapshot from 20080331 and Bingo! I'm sending this to you now over hardy/WPA etc.

Maybe this'll do the trick for you.

All the best

M

---

### Post by Hatfield on 2008-04-28
I'm cleaning as we speak.:lolflag:

---

