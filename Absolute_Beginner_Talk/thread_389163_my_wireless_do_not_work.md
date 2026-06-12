---
title: "my wireless do not work"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by IsKall on 2007-03-20
I recently installed Ubuntu 6.10 but my wireless is not installed, when I type in the terminal i got this,

```

iskall@iskall:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:04:33:BE  
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.255  Mask:255.255.255.0
          inet6 addr: xxxx::xxxx:xxxx:xxxx:33be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22086 (21.5 KiB)  TX bytes:5338 (5.2 KiB)
          Interrupt:177 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)


```

it appears to me that my wireless was not installed automaticly during the ubuntu installation. But what am I supposed to do now? I am no good at linux, just know some few commands. Now, how do I install my wireless , because all there is on my wireless homepage was some windows drivers.

BTW, my wireless is an Intel Pro Wireless 2915 if that is some help too you guys.


regards
iskall

---

### Post by KenSentMe on 2007-03-20
Generally the Intel Wireless devices are installed automaticly. With the command iwconfig you get a list of wireless devices on your system. You could check if your wireless connection is listed there. 

If it is listed, go to System > Administration > Network and try to configure your wireless network.

---

### Post by IsKall on 2007-03-20
Yeah the wireless is shown at iwconfig and netoworking, but it can't find any wireless routers, my wireless router has also been "reseted" so it wont require wpa password, just too see if it can connect, but the wireless do not find any wrouters, and it should be plenty of them.

this was shown in iwconfig.

```

iskall@iskall:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Brusk"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

Something tells me that 
"RTS thr" , "Fragment thr" and "Power Management" should not be off? But thats only a guess.

---

### Post by KenSentMe on 2007-03-20
Try installing the package netwok-manager-gnome through the following command:

```
sudo apt-get install network-manager-gnome

```

Then restart your computer and in the taskbar there should be an icon for the networkmanager applet. Click it and see if it finds your network.

---

### Post by IsKall on 2007-03-20
Already done that, it only finds my wired connection. Kinda weird, in dapper it worked perfectly.

---

### Post by IsKall on 2007-03-20
anyone who knows what the problem may be?

---

### Post by Kamu on 2007-03-20
You have an ESSID labelled "Brusk" listed after iwconfig which the name of the network/access point that the card is looking for.  Make sure it matches the wireless router you are trying to connect to (yes, this is case-sensitive).  You can also set it to auto if you want to look for networks automatically.

I'm not sitting at my Ubuntu computer right now so the following is from memory and I recommend you check the man pages for correctness before trying any of this.
dhcpclient eth1 restart
or doing 
ifdown eth1
ifup eth1

will take down and restart network interface eth1.

If you still cannot connect, you can post the output of those commands as well as the content of /etc/network/interfaces to help us here with diagnosis.

---

### Post by KenSentMe on 2007-03-21
Maybe it's also a good idea to post the contents of the file /etc/network/interfaces.

---

