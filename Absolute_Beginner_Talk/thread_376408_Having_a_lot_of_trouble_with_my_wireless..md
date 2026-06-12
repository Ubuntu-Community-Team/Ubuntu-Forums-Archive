---
title: "Having a lot of trouble with my wireless."
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by TopHatCat on 2007-03-04
I just installed Ubuntu for the first time today so I'm really new to this.

I'm having a lot of difficulty getting my Laptop to connect to my Linksys wireless router which is running WEP encryption.

I've tried going to "System -> Administration -> Networking" and putting my WEP key and whatnot into my Wireless Connection's properties but I can't change my connection from eth0 to something else and realize I'm probably going about it all wrong anyway.

Can anyone offer any guidance in getting my wireless connectivity up and running? :)

---

### Post by mozkaynak on 2007-03-04
Hi,

This is what I do to get connected any wireless:

I use wifiradar (available in the repository)

i choose my wireless and click on connect. It may ask you to create a profile. You can also enter WEP key here (I am not sure about that, I use only free wireless in cafehouses).
then I goto system->admin.->networking and choose wireless card then click properties. choose the wireless you want to get connected and configure it.

as default gateway it is not always necessary to put anything but i should be a good practice to change it to wireless.
it configures things for 30 sec. or so then you are ready to go
I use dappler drake BTW

---

### Post by TopHatCat on 2007-03-04
Where do I find the repository?

---

### Post by lemoniceblock on 2007-03-04
First make sure that the repositories are enabled by going to System>Administration>Software Sources and make sure whichever repository that wifiradar is on is checked (I usually check multiverse, universe and main).
Then go to Applications>Add/Remove>Internet and you should find Wifiradar there.

---

### Post by TopHatCat on 2007-03-04
Oh, wow! I didn't even know all that stuff was there! ^_^

Thats a huge help. Guess I have a lot of apps to look through now...  lol  :D  Lets see if I can figure out this wi-fi problem now. I was wondering why I couldn't get Ubuntu to look for wireless networks in the area...

---

### Post by freeflyer57 on 2007-03-04
Is the eth1 configured or activated?

If eth1 is not configured, then highlight wireless connection and click properties->Enable this connection->add ESSID and WEP key. Leave configuration as DHCP. Click ok.

Then highlight wireless connection and click activate. If al info is correct it shouldn't take long.

---

### Post by TopHatCat on 2007-03-04
I still can't seem to pull an IP address from my router, though...

I webbed into my router (192.168.1.2 on my network) and copied the WEP key into the WiFi Radar info but I still can't seem to connect. :(

---

### Post by fdrake on 2007-03-04
open the terminal and type:
iwconfig
paste here your output.

---

### Post by TopHatCat on 2007-03-04
> **freeflyer57 said:**
> Is the eth1 configured or activated?

If eth1 is not configured, then highlight wireless connection and click properties->Enable this connection->add ESSID and WEP key. Leave configuration as DHCP. Click ok.

Then highlight wireless connection and click activate. If al info is correct it shouldn't take long.

Both eth0 (wired) and ath0 (wireless) are enabled in my Network Settings. Then if I go down to my taskbar to select ath0 as my active connection (which is currently eth0) I can't change to ath0. It doesn't appear on the list of connections. Only eth0 and lo are on the list.

---

### Post by TopHatCat on 2007-03-04
ath0      Link encap:Ethernet  HWaddr 00:11:F5:7A:C4:EA  
          inet6 addr: fe80::211:f5ff:fe7a:c4ea/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10126 (9.8 KiB)  TX bytes:18768 (18.3 KiB)

eth0      Link encap:Ethernet  HWaddr 00:0F:B0:8F:9C:2C  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe8f:9c2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34972 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52365859 (49.9 MiB)  TX bytes:4036858 (3.8 MiB)
          Interrupt:193 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1100 (1.0 KiB)  TX bytes:1100 (1.0 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-F5-7A-C4-EA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78536 errors:0 dropped:0 overruns:0 frame:5863
          TX packets:34403 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:7244664 (6.9 MiB)  TX bytes:1619578 (1.5 MiB)
          Interrupt:201 Memory:f8aa0000-f8ab0000


Curious why ath0 and wifi0 are listed as two separate connections.

---

### Post by fdrake on 2007-03-04
sorry but i canged the word you gave me the output for ifconfig i need the output for iwconfig..

---

### Post by TopHatCat on 2007-03-04
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Nirvana"  Nickname:"Nirvana"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:48 Mb/s   Tx-Power:13 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/94  Signal level=-46 dBm  Noise level=-95 dBm
          Rx invalid nwid:664  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by fdrake on 2007-03-04
is nirvana your essid?

---

### Post by TopHatCat on 2007-03-04
> **fdrake said:**
> is nirvana your essid?

Nirvana is the name of my 802.11g Linksys Router so... yes.

---

### Post by TopHatCat on 2007-03-04
AH HAH!

I finally figured it out. I was putting my WEP key into my WiFi Radar information as well as in my Network Settings. As soon as I removed the key from my WiFi Radar settings and set everything up to auto-negotiate I was able to pull an IP address.

A big THANK YOU to everyone in this topic. I'm loving this community. :)

---

