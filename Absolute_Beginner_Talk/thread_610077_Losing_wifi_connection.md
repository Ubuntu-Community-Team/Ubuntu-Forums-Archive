---
title: "Losing wifi connection"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by 01steven on 2007-11-11
Been running Ubuntu for about a week now on my home laptop.
No problem finding and connecting to my wireless router (I have an Orange Livebox here in UK if that's relevant).
Tonight the wifi connection kept dropping.
It kept asking me for the WEP key.
I kept putting in the right WEP key but it still wouldn't connect.
Rebooted the router and it reconnected, but not long after it dropped connection again (well actually went to 30%, then 0%).
I have a wifi portable device (my Nokia N95 mobile), which also seems to find then lose the connection.
So if my phone isn't latching onto the network (which is always 100% solid), then the fault must be something to do with the network, rather than the laptop/Ubuntu?
I called Orange and surprise surprise they couldn't help me as they didn't support Linux or my mobile, only Windows!
I've now had to plug in the ethernet cable to get a connection- most annoying! But I suppose it proves the broadband connection is OK.

Anyhow, I had a look at the list of available wireless networks. I live in a block of flats and there's normally 3 or 4 other (secure) networks visible.
But I'm sure there's a couple of networks in the list I've not seen before.
And I'm wondering if they're somehow interfering with my connection.
Is there some way in Ubuntu to block out other connections, or make my wifi connection take precedence?

Regards

---

### Post by mkoehler on 2007-11-11
Steven,

     Are you experiencing interference with another network with the same ESSID or do the other networks have different ESSIDs?

---

### Post by 01steven on 2007-11-11
> **mkoehler said:**
> Steven,

     Are you experiencing interference with another network with the same ESSID or do the other networks have different ESSIDs?

Didn't know what an ESSID was - but wikipedia helped on that one!
No, the other network(s) have different names to mine.

---

### Post by RTSnLV on 2007-11-11
Could be a number of things, did you recently buy a new cordless phone?" Try changing the channel that the router broadcasts on. It might be your router is dying. Considering its effecting multiple devices its a signal problem

---

### Post by P4man on 2007-11-11
The network names are not that important, the channel you use is. If another nearby network (or other device) is transmitting on the same channel (=frequency), you could get connection problems.

 You should be able to configure a channel on your router (usually between 1 and 12).  The clients will adjust automatically, no need to configure anything there. So try changing  channels.

Ideally you should run an app that scans all networks and gives you the channel, but I havent found something like that for Linux.

---

### Post by 01steven on 2007-11-11
No new cordless phone, no.
Maybe I need to have a look at the settings for it and see if I can move it onto another channel?

---

### Post by 01steven on 2007-11-11
No new cordless phone, no.
Maybe I need to have a look at the settings for it and see if I can move it onto another channel?
It's only a couple of months old so would be surprised if it were dying.

---

### Post by mkoehler on 2007-11-11
To get the channel frequencies, run:
```
sudo iwlist <device_name> scan
```

where <device_name> is the name of the network device that is scanning.  For example, I run the command sudo iwlist eth1 scan which gives me information about every channel found in range of your computer.  If you see conflicting channel numbers when you run this command, I would change the channel that your router uses, as suggested above.

Cheers!

---

### Post by 01steven on 2007-11-11
Couldn't get that code to work.
Kept saying <device-name> Interface doesn't support scanning.

Anyhow I changed the channel via my router settings.
So far, so good- it is holding.
But the idea of being able to see which channel the other networks are on is very appealing, and I'd still like to work this out if possible.

---

### Post by P4man on 2007-11-11
try

```
ifconfig
```

to get the names of your devices. Your wireless is probably called wlan0

---

### Post by RTSnLV on 2007-11-11
download kismet

---

### Post by kwacka on 2007-11-11
Try kismet - a passive packet sniffer - it'll tell you everything that's going on around you.

---

### Post by 01steven on 2007-11-12
Sounds good, but it's not in the repository.
Don't feel comfortable downloading software not there, unless you can explain how?

---

### Post by P4man on 2007-11-12
Not only is it not in the repository, it is also not packaged, so you have to compile and load it yourself, and it might not even work with your wifi card. All that may be a bit overkill for your problem and intimidating for a new linux user, just stick with command given above, it is all you need.

---

### Post by 01steven on 2007-11-12
> **P4man said:**
> try

```
ifconfig
```

to get the names of your devices. Your wireless is probably called wlan0

steven@steven-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:3F:64:9A:4F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:04:23:67:CA:FE  
          inet addr:192.168.1.159  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fe67:cafe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6290 errors:13 dropped:13 overruns:0 frame:0
          TX packets:5618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6503115 (6.2 MB)  TX bytes:1178119 (1.1 MB)
          Interrupt:5 Base address:0x2000 Memory:90000000-90000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

steven@steven-laptop:~$ 



What does this say about other networks?

---

### Post by P4man on 2007-11-12
> **01steven said:**
> 
What does this say about other networks?

Nothing whatsoever, it was just to determine the device name of your wifi adapter. It appears to be eth1 -I always thought wlan adapters where named wlanX.. That is what they are called on 3 of my machines, so I'm not sure why yours is different. Maybe someone can shed a light on this ?

Anyway, to get info on other networks, the command would then simply be:

```
sudo iwlist eth1 scanning
```

But I just tried on my laptop, and I also get "interface doesn't support scanning". I think it has to do with the wifi driver supporting some sort of special mode, which is also required by these packet sniffers like the one linked above, so I am guessing these won't work either on our machines?

---

