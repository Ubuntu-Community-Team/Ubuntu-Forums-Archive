---
title: "Planning On Trying out Ubuntu."
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Dvorakis on 2007-05-16
I know a simple bit about computers themselves...and windows...but want to learn stuff about linux.

I want to try ubuntu,last time i tried I had a successful install and everything worked dandy...except the internet.When I would try to connect the it it would start to connect and then stop before completing...and I forgot to set up a partition so it did not work out well...no im trying again.Im sure if I can get the internet to work i'll be happy this time.So Im going to try installing again...this time with a partition.

So I plan to set up a partition but i have some questions....when I set up a partition will i have the ability to choose what I boot on when the computer starts?And what about my old internet problem....what might have caused that?

Is there anything else I need to find out before installing ubuntu?

---

### Post by chamberlain2006 on 2007-05-16
Hello, and I'm glad to hear that you're trying out Ubuntu/Linux.  Grub will automaically detect other operating systems, and allow you to choose which one to boot.  About your network problem, It may just be that your release was old, and that a driver wasn't ready or perfected for your card.  You should try out the LiveCD and see if it works there.  If not, come back and we'll see what we can do.  Good luck!

---

### Post by ThePolemistis on 2007-05-16
> **Dvorakis said:**
> I know a simple bit about computers themselves...and windows...but want to learn stuff about linux.

I want to try ubuntu,last time i tried I had a successful install and everything worked dandy...except the internet.When I would try to connect the it it would start to connect and then stop before completing...and I forgot to set up a partition so it did not work out well...no im trying again.Im sure if I can get the internet to work i'll be happy this time.So Im going to try installing again...this time with a partition.

So I plan to set up a partition but i have some questions....when I set up a partition will i have the ability to choose what I boot on when the computer starts?And what about my old internet problem....what might have caused that?

Is there anything else I need to find out before installing ubuntu?

the internet connection shouldnt hav anything to do with ur partition.
You can have options on what to boot, but it requires more work... i have the windows boot screen laoding with the option of loading grub (im using boot.ini file as the boot laoder). My default is windows. when grub is clicked it goes to the linux bootscreen (ie. grub)

Your old internet connection problem may have been due to not having the driver for it... was it a modem?, because the only time the internet did not work for me on linux, was when i used to have a modem.
If its a network card,,, u will be perfectly okay --i tihink :P.

---

### Post by Dvorakis on 2007-05-17
Thanks,I just got the latest release and will try internet out.Im using a wireless router from netgear,so lets see what happens.

---

### Post by Dvorakis on 2007-05-17
Just tried it out...didn't work.I don't know why.It starts to connect and then stops.

I have a netgear WGR614v6 router.Any help?

Internet card is WG311v2

---

### Post by lemmy999 on 2007-05-17
Dvorakis

Welcome to ubuntu!

You are really trying to make things pretty difficult for yourself. Most manufacturers of wireless cards etc do not support Linux out of    the box ( with the exception of Cisco)

Can you get an ethernet connection to your computer? That will make things easier. After that you can take the time to learn about ndiswrapper to make your wireless card work with Ubuntu

good luck. Stick with it- it really is worth it!:)

---

### Post by Dvorakis on 2007-05-17
I checked out the card...it says it should be supported out of the box.I don't have any extra cables so wired is a no go.But i just tried again,I got it to actually connect to my card,but it wouldn't actually get the internet.(I was connected but I couldn't browse)

Any help?

---

### Post by Dvorakis on 2007-05-17
Bump....please help.It says Im connected to my wireless network...but it won't connect to any website.It says unable to access page.

---

### Post by teknosexual on 2007-05-17
Have you checked your firewall settings? Any MAC filters or anything like that in place?

---

### Post by Dvorakis on 2007-05-18
MAC filters?Sorry your going to have to explain more to me about this.

---

### Post by Pinger05 on 2007-05-18
Make sure you set your default gateway to the IP address of your wireless router.  Also ensure you DNS server is the IP address of the router.  Unless you changed the configuration it is probably 192.168.1.1.  Just put those IP addresses in the:

Default Gateway
and
DNS

Places you will be golden!  BTW Ubuntu is way cooler than Vista.  My 10 year old doesnt like Vista anymore, he loves Ubuntu!

---

### Post by Parmenion on 2007-05-18
AFAIK, with MAC filtering enabled, he shouldnt even be able to get a connection to the router. 

Dvorakis, I think you really need to borrow another machine's ethernet cable and grab ndiswrapper from the repos or compile the newest version from source. 

OR

You could install Wicd(pronounced as wicked). Using a combination of Wicd and Ndiswrapper helped to clear up my wireless problems. Wicd can be found [here]("http://wicd.sourceforge.net/").

---

### Post by steve.horsley on 2007-05-18
Before doing anything dramatic, try posting the output from these commands:
[B]iwconfig
ifconfig
sudo dhclient
route -n[/B]

---

### Post by Dvorakis on 2007-05-18
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"NETGEAR"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=31/100  Signal level=4/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:CC:28:D8:2B  
          inet6 addr: fe80::2a0:ccff:fe28:d82b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:48 dropped:0 overruns:0 carrier:96
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xd000 

eth1      Link encap:Ethernet  HWaddr 00:40:CA:4A:9D:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5228 (5.1 KiB)  TX bytes:5228 (5.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:80:9B:BC  
          inet6 addr: fe80::20f:b5ff:fe80:9bbc/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76 (76.0 b)  TX bytes:520 (520.0 b)
          Interrupt:17 

sudo dhclient
Listening on LPF/wlan0/00:0f:b5:80:9b:bc
Sending on   LPF/wlan0/00:0f:b5:80:9b:bc
Listening on LPF/eth1/00:40:ca:4a:9d:12
Sending on   LPF/eth1/00:40:ca:4a:9d:12
Listening on LPF/eth0/00:a0:cc:28:d8:2b
Sending on   LPF/eth0/00:a0:cc:28:d8:2b
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 wlan0


Theres what I got...about NDISwrapper,I can get it on there from the website I think...Can I transfer it through with my flashdrive?

---

### Post by tyboon on 2007-05-18
I am using feisty fawn and i use a router to connect..level one.... 
I really cant understand why..it should be working auomatically..I agree with a previous post that you should try with ethernet...
But keep on trying...I had my difficulties when i changed from Xp to linux...It took me about 5 days to get it on working...but it really paid up...:guitar:

---

### Post by Dvorakis on 2007-05-19
Ok,i plan on getting it to work.

Any more help?

---

