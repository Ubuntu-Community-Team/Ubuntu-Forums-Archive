---
title: "Cannot connect to internet"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Bandolin on 2007-12-28
Ok, I know there are no less than 5 threads with similar titles, and I've read them all, but they don't address my specific problem in any way that I can understand.

So here it goes. I have an ADSL Gnet modem connect via Ethernet. The following is my ifconfig

bandolin@bandolin-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:F4:38:6D:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0x8c00 

eth1      Link encap:Ethernet  HWaddr 00:11:D8:0E:67:70  
          inet6 addr: fe80::211:d8ff:fe0e:6770/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9814 (9.5 KB)  TX bytes:5699 (5.5 KB)
          Interrupt:17 

eth1:avah Link encap:Ethernet  HWaddr 00:11:D8:0E:67:70  
          inet addr:169.254.5.184  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

bandolin@bandolin-desktop:~$ 


I noticed in the other threads people were asking users to post their ifconfigs, so I'm doing so in advance if its any help. From the other threads they imply that an ethernet connected modem should autoconfig itself. But even in Windows I had to input my Username and Password for my ISP. I can't find were to do this in Ubuntu.

---

### Post by blueridgedog on 2007-12-28
If you have a username and password from your ISP and you have DSL, I would wager that you need to use pppoe.

I do not have a user name based DSL account, so I can not go through the process to see what steps there might be, but to start configuring pppoe your run the following in a terminal:

sudo pppoeconf

See:

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

Perhaps others with pppoe setups can help.

---

### Post by autocrosser on 2007-12-28
I have a DSL modem & this is what I did to side-step the problem....

Bought a cheap internet gateway router (Linksys 54XX)
used the wireless ability & installed a wireless card in both of my desktops.

Using the firewall functions of the router & the wireless ability to run several computers off of the connection. There is no direct connection between the router & either of the desktops.

Minimum config.....Network Manager created a Ad-hoc network within the first 30 sec of my desktop start....

---

### Post by horry on 2007-12-28
> **blueridgedog said:**
> If you have a username and password from your ISP and you have DSL, I would wager that you need to use pppoe.

I do not have a user name based DSL account, so I can not go through the process to see what steps there might be, but to start configuring pppoe your run the following in a terminal:

sudo pppoeconf

See:

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

Perhaps others with pppoe setups can help.

i agree with you. i use adsl too. pppoeconf is used for connecting to internet. 
check the status of connection when you power on the adsl modem, of course, you can use internet directly, if you can set the modem to auto dial when power on. otherwise, type 'sudo pppoeconf' in a terminal, just finish the configuration, you will be requested to fill username and password. the pppoeconf just set once. you can use 'pon dsl-provider' and 'poff dsl-provider' to connect and disconnect to internet.

good luck.

---

### Post by Bandolin on 2007-12-31
Thanks for the suggestions. I'll give those a go and report if it worked for future users who may have similar problems.

I gave sudo pppoeconf a try and it held my hand through a series of dialogs. I clicked Ok on all of them as it was suggested. I entered my Username and Password as given to me by my provider. Checked the spelling 4 times to make sure it was right with no type-Os.

Typed plog and got this:
bandolin@bandolin-desktop:~$ plog
Dec 31 12:14:51 bandolin-desktop pppd[6177]: Unable to complete PPPoE Discovery
Dec 31 12:15:10 bandolin-desktop pppd[6454]: Plugin rp-pppoe.so loaded.
Dec 31 12:15:10 bandolin-desktop pppd[6456]: pppd 2.4.4 started by root, uid 0
Dec 31 12:15:10 bandolin-desktop pppd[6456]: PPP session is 5122
Dec 31 12:15:10 bandolin-desktop pppd[6456]: Using interface ppp0
Dec 31 12:15:10 bandolin-desktop pppd[6456]: Connect: ppp0 <--> eth1
Dec 31 12:15:12 bandolin-desktop pppd[6456]: PAP authentication failed
Dec 31 12:15:12 bandolin-desktop pppd[6456]: Connection terminated.
Dec 31 12:15:28 bandolin-desktop pppd[6466]: Plugin rp-pppoe.so loaded.
Dec 31 12:15:28 bandolin-desktop pppd[6468]: pppd 2.4.4 started by bandolin, uid

I have not idea why authentication failed. I am absolutely positive I entered User name and password correctly. I checked with my ISP to ensure I have the correct Username and Password and he assured me I do. He went so far to tell me that if I get the PAP authentication failed notice, that I'm connecting to the Server but I don't have the right drivers or whatever. He was knowledgeable in Linux, and was even familiar with Ubuntu, but stopped short of giving me specific answers as they do not support Linux. =(

---

### Post by Bandolin on 2008-01-03
Still trying to connect to the internet via PPPoE with no joy. This is definitely an Ubuntu issue because I had no problems connecting with Knoppix.

---

### Post by Bandolin on 2008-01-04
I solved my problem and I think the Ubuntu staff should take note of this.

I could not log in to my ISP after I configured my PPPoE connection because of the following oversight.

When the dialog that asks you to input your user name the word "User Name" **is in the field**. So, I simply typed my User name after it. 

Example: If my user name was HelloDolly, My ISP received: _User name: HelloDolly_.

You must delete the *User name* text and ensure only the characters of your user name appear in the field.

Funny how it doesn't happen with Password. The field is blank allowing you to type in your password without having to delete any prior text.

---

### Post by blueridgedog on 2008-01-04
Well done.  I have been following the thread, but unable to offer any other suggestions because I could not mockup the failure.  Good work.

---

