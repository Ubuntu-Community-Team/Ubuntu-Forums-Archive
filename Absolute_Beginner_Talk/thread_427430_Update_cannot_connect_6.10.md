---
title: "Update cannot connect 6.10"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by rpaco on 2007-04-29
Running Ubuntu 6.10. My Firefox and Skype connect to the Internet ok but neither Evolution or any of the update methods ie Add/Remove Snaptic and apt-get in a terminal; these all just time out.

I am running an external Syslink  ADSL2MU modem/single port router which is connected via my ethernet port. 

I have blacklisted ipv6 to enable Firefox to connect (without it blacklisted nothing at all can connect). Any suggestions please.

---

### Post by Kobalt on 2007-04-29
Does your router have a built-in Firewall that's activated and set ? Are there any ports set to be blocked within its configuration ?

---

### Post by rpaco on 2007-04-29
No no firewall as far as I know, if it's any help here is the ifconfig readout:
 
Link encap:Ethernet  HWaddr 00:19:66:0F:24:6C  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5646595 (5.3 MiB)  TX bytes:691577 (675.3 KiB)
          Interrupt:201 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

---

### Post by rpaco on 2007-04-30
Any other ideas please, just tell me where to look and what to type in terminal and results to post like dhcp or whatever. 

Meanwhile I will see if Thunderbird can be installed and connect, (I note it is on the install CD.)  if so I will have to give up on Evolution, pity because it looked quite good. The decent webmail from my IP (force9) only works on IE6 and above so I am stuck with the bargain basement one which is not good. Of course I will still have the problem of updates and installing other things. I am pretty sure it is probably one setting or one line in a file but unfortunately I am spoilt for choice

---

### Post by rpaco on 2007-04-30
Strange, although Thunderbird is on the installation CD (burned from the downloaded ISO) it appears to be in windows format with setup.exe which will not run in Ubuntu. I'm sure there is an explanation for this. However I have now downloaded the tar.gz and will try with that.

---

### Post by guitarchris on 2007-05-16
Hi. I'm pretty new to all this but I had a similar prob with Mepis (which is, as you may know, based on Ubuntu). I decided to try Feisty Fawn and waddayaknow  everything works now (including my camera which Mepis couldn't do either. I'm actually using Ubuntustudio but I'm sure the standard distro will work just as well.
This is by far the best distro I have ever tried and I 'm beginning to think I can sling W2k in the bin at last!
I suggest you upgrade.
Hope this helps!
:guitar:

---

