---
title: "Can't connect to the Internet"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by shyopstv on 2006-04-04
This is following on from [this thread]("http://www.ubuntuforums.org/showthread.php?t=154461") Cheers to anyone who helped me there. If you didn't then here's your chance ;)

I connect to the internet using a wirless USB adpapter which makes a connection with the router. I have installed the drivers for the router and can configure my computer to connect to the network I need but when I open up Firefox I just get "page cannot be found" I tried pinging stuff but that doesn't work either. I know the network is working because I can use it in Windows and I know that it is configured correctly because I just copied everything over from Windows

Thanks

---

### Post by waster on 2006-04-04
can you ping your router?
what is in /etc/resolv.conf
what does the command "route" tell you (is there a delay when you enter this command?)

---

### Post by AndyCooll on 2006-04-04
As mentioned above your resolv.conf needs to have a line in it saying something like:

Nameserver 192.168.0.1

Where the IP address is that of your router.

Also what does your /etc/network/interfaces file say?

:cool:

---

### Post by jamesr on 2006-04-04
I am puzzled by your suggestion that the nameserver need to be> Nameserver 192.168.0.1 because I am assuming that is the address on the router. The nameserver needs to be DNS server on the ISP, surely?

I, personally would add ```
sudo ifconfig -a
```

---

### Post by shyopstv on 2006-04-04
Just sone some of the stuff you mentioned:

/etc/resolv.conf is blank


/etc/network/interfaces file says:

```

# The loopback network interface
    auto lo
    iface lo inet loopback

# This is a list of hotpluggable interfaces. They will be activated automatically by the hotplug system

    Mapping hotplug
    script grep
    map eth0

iface wlan0 inet dhcp
wireless-essid NAME

auto wlan0
```


sudo -iconfiig -a comesup with three paragraphs so I just chose the one which started with wlan0 :)

```

wlan0

link encap: Wthernet HW addr 00:0F:B3:F4:03:59
UP BROADCAST MULTICAST MTU: 1500 Metric: 1
RX Packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
TX Packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0 collisions: 0 txqueuelen: 1000 
RX bytes: 0 (0.0 b) TX bytes: 0 (0.0 b)

```


I haven't done the route thing yet (I have to reboot into Ubuntu whenever I want to do something so it is easy to forget some stuff :) ) but hopefully that should be enough for you to be able to help me

---

### Post by shyopstv on 2006-04-04
I have just done route. It does not take take ages and produces a routing table with nothing in it.

Ahhhhhh ](*,)

---

### Post by jamesr on 2006-04-04
The file /etc/resolv.conf should look like

> nameserver xxx.xxx.xxx.xxxmay two lines where xxx.xxx.xxx.xxx are the addresses of the DNS servers for your ISP. This often on the main page of their web site.


```
sudo dhclient wlan0
``` then check the output of ```
sudo ifconfig -a
``` it should have changed

```
ping 192.168.0.1 
``` where 192.168.0.1 is the address of your router

---

### Post by shyopstv on 2006-04-04
Thanks

I have the ISP numbers for the DNS servers, how do I change resolv.conf so it lists them?

---

### Post by jamesr on 2006-04-04
```
sudo nano /etc/resolv.conf
```

type in the lines , control X to exit, answer questions appropriately.

BUT do check ```
sudo iwconfig -a
``` or ```
sudo ifconfig -a
```to see if the NIC is being seen.

---

### Post by shyopstv on 2006-04-05
I have put the DNS addresses into resolv.conf but the output from ifconfig has not changed. iwconfig -a just says "-a no such device" and I cannot ping my router (it says the network is unreachable)

dhclient wlan0 says tht no DHCPOFFERS are recieve after it does all the DHCPDISCOVR stuff and that there are nor working leases in peristent database :confused:

---

### Post by shyopstv on 2006-04-05
Anybody?

---

### Post by jamesr on 2006-04-05
What is your router or are you just using a adsl modem? or combined?
```
sudo iwconfig
``` instead of adding the -a

If a router , what type?
If a ADSL modem
```
sudo pppoeconf
```and supply isp and a user information.

---

### Post by shyopstv on 2006-04-05
The router I have is an Actiontec 54Mbps Wireless Cable/DSL Router ([This one]("http://www.actiontec.com/products/home_networking/54mbps_wireless_router/index.php") in fact). I am not sure what I am supposed to put in instead of -a

Thanks

---

### Post by jamesr on 2006-04-05
just sudo iwconfig this should select the wireless configs

---

### Post by shyopstv on 2006-04-05
Just did that:

```
IEE: 802.11-DS   ESSID: "home"   Nickname: "Unknown"
Mode: Managed   Bit Rate = 54Mbps   Tx-Power: 32dBm
Encryption key: off
Power management: off
Link quality: 0   Signal level: 0   Noise level: 0
Rx invalid noid: 0   Rx invalid crypt: 0   Rx invalid frag: 0
Tx excessive retries: 0   Invalid misc: 0   Missed beacon: 0
```

---

### Post by shyopstv on 2006-04-05
Sorry to keep bumping the thread but does anyone know how I could solve this problem?

---

### Post by AndyCooll on 2006-04-05
I repeat what I said earlier. Edit resolv.conf and add the following:

search nameofyourhomedomain
nameserver 192.168.0.1 (or whatever is the IP address of your router)
domain nameofyourhomedomain

then restart the service (or reboot the computer)

The information you were given earlier about DNS addresses was incorrect. It is true that your IP service dishes out an address for your overall internet service, but that is held by your router. It is your router that then directs the traffic around your home network, **AND** it is very likely that it is your _router_ that handles IP addresses on your home network. Hence why for computers on your network that it is your router that is your nameserver. 

I have four boxes running on my homel network through a router. And this is what the resolv.conf says on all of them. Plus, I had a similar issue when I once installed SUSE (and later Fedora) and could happily get on to my internal network but not get the Internet. I went on to their forums and this is what they said to do. Did that and had the Internet in no time.

Try it. You've got nothing to lose!

---

### Post by shyopstv on 2006-04-05
OK extremly stupid question time. What do you mean by "name of your home domain"

Thanks

---

### Post by AndyCooll on 2006-04-05
By that I mean the name of your network/group/workgroup/domain name/whatever you call it. If you have more than one computer, to be able to share they should all be in the same workgroup/domain. That name.

You may not need to include those, I'm not sure if they are vital or not (something tells me they aren't). Your resolv.conf might just have the one line "Nameserver 192.168.0.1"

---

### Post by shyopstv on 2006-04-06
It still doesn't work. I'm beginning to think that it might be easier to try another distro. Does anyone have any suggestions?

---

### Post by jamesr on 2006-04-06
I have reread the posts and noticed that you have no routing table, sorry about the delay but I will post instructions.

---

### Post by Iowan on 2006-04-06
[QUOTE=shyopstv]It still doesn't work. I'm beginning to think that it might be easier to try another distro. Does anyone have any suggestions?[/QUOTE]Sure, threaten to go elsewhere... that'll win friends (it's even more effective to threaten to run back to M$).  ;) 

Did you ever get a ping response from the router?  I suspect it'll be an uphill battle until you can at least ping it via IP address.  Part of the ping issue might be no IP address (I think this has already been mentioned).  Is there a DHCP Server on your net (the router)?  You could try forcing a static address to see if connectivity improves (details?), but you'll need to know the local net address (subnet).  Lots of details to attend to, but look at the education you're getting for (almost) free...

---

### Post by shyopstv on 2006-04-07
Sorry it has taken me so long to get back to this

I have set up a static IP address and there is still no difference. Now when I try to ping my router I get many lines saying that it is unreachable instead of just one... I can ping myself which is a start :mrgreen: :rolleyes: 

Interestingly before I set it up, the "configuring network connection" part of the boot-up stage took ages now it doesn't but the  "synchronising clock" bit does instead

---

### Post by dvarsam on 2006-04-08
Give us the output of your "ifconfig -a"!!!

If you want to be "cryptic" & do NOT provide info to us, how the heck do you want us to help you man...?

And _listen_ to what people tell you to do... man...

You are NOT listening...

People are _asking_ from you feedback which you do NOT provide!!!

NOT only that, but I read that you are doing this & that, while NOT really doing what the people who are trying to help you suggest...!!!

If you want help, do what you are told & _provide_ feedback.

Do NOT say just "I did it"...

_Submit_ the output results you get, into this Forum man...!!!

And do NOT screen out some of the results, because _YOU_ think that they are irrelevant!!!

Good Luck!

---

### Post by shyopstv on 2006-04-08
WTF?! What brought that on?

I have already said what ifconfig -a comes up with in the fifth post in the thread:

wlan0

link encap: Wthernet HW addr 00:0F:B3:F4:03:59
UP BROADCAST MULTICAST MTU: 1500 Metric: 1
RX Packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
TX Packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0 collisions: 0 txqueuelen: 1000 
RX bytes: 0 (0.0 b) TX bytes: 0 (0.0 b)

The other two pragraphs come out with stuff about my other connections, not my wireless connetion. I have no connection to the Internet through Ubuntu therefore the only way I can post my output here is to write it all down on a piece of paer and copy it up here which takes ages if you have pages of stuff. I have always mentioned when I have left stuff out and if that is important then people can always tell me

While you are accusing me of being crytic and vague, could you please tell me where I have not given feedback that was asked for or where I have done something different to what they told me to do? And instead of screaming at me for not supplying the necessary information could you tell me what the necessary information is? If not then don't bother posting.

---

### Post by shyopstv on 2006-04-08
Aside from that post:

I set it up to give me a static IP address of 192.168.0.253 and changed my router so the DCHP ips go between 192.168.0.2 and 192.168.0.250 I think that that's what you are supposed to do right? Whilst I was doing that I set my Windows boot to a static IP of 192.168.0.254 and that is working and I am using the same DNS servers in both so I don't think that that is the problem

When I try to ping 192.168.0.1 in terminal (the default gateway. I think that is my router's ip. When I type it into IE, I get the router configuration page) I get a loong list of lines:

```
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data
From 192.168.0.253 icmp_seq=2 Destination Host Unreachable
From 192.168.0.253 icmp_seq=3 Destination Host Unreachable
From 192.168.0.253 icmp_seq=4 Destination Host Unreachable
From 192.168.0.253 icmp_seq=6 Destination Host Unreachable
From 192.168.0.253 icmp_seq=7 Destination Host Unreachable
From 192.168.0.253 icmp_seq=8 Destination Host Unreachable
From 192.168.0.253 icmp_seq=10 Destination Host Unreachable
From 192.168.0.253 icmp_seq=11 Destination Host Unreachable
From 192.168.0.253 icmp_seq=12 Destination Host Unreachable
From 192.168.0.253 icmp_seq=14 Destination Host Unreachable
From 192.168.0.253 icmp_seq=15 Destination Host Unreachable
From 192.168.0.253 icmp_seq=16 Destination Host Unreachable
```

And so on....


Due to setting up the static ip, I noticed the ifconfig -a has changed slightly. I finally got around to setting up my printer (I was shocked at how easy it was) so here for your enjoyment (;) ), is the entire ifconfig -a!

```

eth0    Link encap: Ethernet   HWaddr: 00:20:ED:B8:DD:8E
          BROADCAST MULTICAST   MTU:1500    Metric: 1
          RX packets:0   errors:0    dropped:0   overruns:0   frame:0
          TX packets:0   errors:0    dropped:0   overruns:0   carrier:0
          collisions:0   txqueuelen:1000
          RX bytes:0 (0.0 b)   TX bytes:0 (0.0 b)
          Interrupt: 17   Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1   Mask:255.0.0.0
          UP LOOPBACK RUNNING   MTU:16436   Metric:1
          RX packets:4961   errors:0    dropped:0   overruns:0   frame:0
          TX packets:4961   errors:0    dropped:0   overruns:0   carrier:0
          collisions:0   txqueuelen:0
          RX bytes:427712 (417.6 KiB)   TX bytes:427712 (417.6 KiB)

wlan0   Link encap: Ethernet   HWaddr: 00:0F:B3:F4:03:59
          inet addr:192.168.0.253   Bcast:192.168.0.255   MasK:255.255.255.0
          BROADCAST MULTICAST   MTU:1500    Metric: 1
          RX packets:0   errors:0    dropped:0   overruns:0   frame:0
          TX packets:0   errors:0    dropped:0   overruns:0   carrier:0
          collisions:0   txqueuelen:1000
          RX bytes:0 (0.0 b)   TX bytes:0 (0.0 b)
          Interrupt: 17   Base address:0xdc00

```


I am currently going through the troubleshooting article on the wiki ([https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)) and it said that you connect to the router by inputting the code ```
sudo iwconfig wlan0 assid home ap 00:0F:B3:F4:03:59
``` Doing this results in absolulty nothing happening. I just get a new line in terminal as if I had just pressed enter without typing anything and the networking aplet in the panel at the bottom still tells me that I am not connected so I am pretty sure that my problem lies with getting connectrd to the router

If you need any more information then please ask

Thanks

---

### Post by rubrboots on 2006-04-08
Hey shyopstv

I am having exactly the same problems as you. I have spent two days screwing around with ubuntu and cant even get on the internet. If you figure it out PLEASE let me know. 


I can ping myself, but not my router. I have changed the reslov.conf to read
-------------------------
namserver 192.168.1.1 
-------------------------

192.168.1.1 is the address of my router. Sorry guys but I cant easily post my ifconfig - a unless i burn it to a cd to transfer the info to a comp with internet, but it is very simular to shyopstv's. I am using a static IP for the ubuntu box.

---

### Post by dvarsam on 2006-04-08
Ok, I have a couple of different ideas on this:

1. Have you tried to setup your LAN through a cable instead of a Wireless connection...
    This could help, maybe to track down what the problem is?
    Is that possible to you, is is your machine far from the Router?
    For Example: Is your Browser working when you are connected Wired - instead of Wireless?

2. For this I am NOT sure, but could this be Related - that IPv6 issue...?
    Maybe you might have to disable it...
    Maybe some Ubuntu Pro (with more knowledge than me) could tell if this 
    could be of an issue...

Hope I helped!

---

