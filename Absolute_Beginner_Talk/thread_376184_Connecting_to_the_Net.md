---
title: "Connecting to the Net"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by c500 on 2007-03-04
Just a few hours into Linux. I am not a technically sophisticated computer user by any means. I am rather proud that, with some inciteful help from forum member. I did manage to create a dual boot and load Ubuntu desktop 6.10.

Now I am trying to set everything up - I can see it will all take some effort. The first task is to get connected with the internet. I wish to use my computers' WIFI (Toshiba Portege 100) to access my linksys router. I would be willing to buy an ethernet cable and cable into the router if it is much easier. Ultimately I wish to use wifi with the PC. I have looked at forums, howto search engines etc but I am not able to follow the suggestions. Writing instructions in terminal is not something I have done or really understand. I have looked at the network GUI but have not been successful. Is there a simple way to accomplish my task (with a GUI prefered) and even simpler instructions?

Many thanks for some tips....and when I am done it will be printers and avoiding the screen resolution to change dramatically after a screen saver comes on!

---

### Post by freeflyer57 on 2007-03-04
system->adminstration->networking

first: highlight wireless connection (eth1) and press properties.

Then : click enable this connection 

third: enter network name exactly the same as the network. If this is not the same it will connect.

If you have a WEP key enter it now.
 
fourth: Leave configuration as DHCP and click OK

fifth: highlight wireless connection and click activate. your internet should now work.

---

### Post by Maxwell Rocatanski on 2007-03-05
I'd like to join in on this thread--I'm running Edgy Eft  on a 15" Titanium Powerbook G4 with the original Airport 802.11b card and I can't seem to get my Airport base station (Original snow version) to successfully assign my laptop an IP address without disabling the WEP key.   The OS X partition connects without issue, so I know the airport card and base station are functional.  What's really wierd is that 6.10 worked flawlessly (plug and play) when I initially installed Ubuntu as the only OS on this laptop--the problem only arose after I reformatted and reinstalled OS X AND Edgy (same exact ISO) as a dual boot setup.

I've updated everything and even installed Wifi-Radar to try and automate the handshake protocol, but I just can't seem to acquire an IP address without disabling WEP security.

I've re-entered (and re-re-entered) the network password in the wireless settings properties.  I've got four other working wireless clients talking to the same network (including the Mac OS X boot partition on this same laptop) so the problem seems to be isolated to Ubuntu.  What's more, it worked flawlessly on the same machine/same build--the only difference is the addition of a Mac OS boot partition.

I'm fairly new to Ubuntu and not all that familiar with terminal commands yet, so if I'm missing something obvious, I'd prefer a GUI solution, if possible.

Thanks in advance,

Maxwell

---

### Post by fdrake on 2007-03-05
when you write the password do you use ascii or hexadecimal type?have you tried both.

---

### Post by Maxwell Rocatanski on 2007-03-05
I've tried both--my other wireless clients use ASCII successfully--but neither seems to successfully connect.

Maxwell

---

### Post by fdrake on 2007-03-05
open the terminal and paste here the outputs of these commands:
ifconfig
iwconfig

---

### Post by Maxwell Rocatanski on 2007-03-05
Here's the output from the IFCONFIG and IWCONFIG commands:

madmax@madmax-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:93:DB:C3:50  
          inet addr:10.0.1.8  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:41 Base address:0x6400 

eth1      Link encap:Ethernet  HWaddr 00:30:65:2C:09:ED  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:669463 (653.7 KiB)  TX bytes:115550 (112.8 KiB)
          Interrupt:57 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4321 (4.2 KiB)  TX bytes:4321 (4.2 KiB)

madmax@madmax-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"mamarosa"  Nickname:"Mamarosa"
          Mode:Managed  Frequency:2.422 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=4/92  Signal level=-93 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:4
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by Maxwell Rocatanski on 2007-03-05
Just "bumping" this thread.  I still need help trying to get my WEP key correctly recognized.  Thanks!

Maxwell

---

