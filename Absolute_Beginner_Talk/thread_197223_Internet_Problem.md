---
title: "Internet Problem"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by jasrog on 2006-06-15
I have tried everything and cannot get online in Ubuntu 6.06. My connection works fine in Windows. Can someone please help?

---

### Post by BitTorrentBuddha on 2006-06-15
Could you provide more detail, are you connecting through wifi or just connected to the modem? What kind of internet do you have? Any other information you can get (of course without posing a security threat to yourself ;))

---

### Post by jasrog on 2006-06-15
I am using high speed internet via cable modem.. when i try to access web i get server not found error. I have done the make sure the box is checked routine in network settings.... i have tried prompts in terminal also unsuccessful..

---

### Post by measure on 2006-06-15
I had a similar problem and when I re-installed Ubuntu it went away. Although I'm sure there is a command you can use in terminal, I'm just not experienced enough to help you any further.

---

### Post by jasrog on 2006-06-15
Yeah I redownloaded LiveCD and tried that but no luck...

---

### Post by allix on 2006-06-15
Try Deactivating and then Activate your network card in System -> Administration - Networking. Or try "sudo dhclient" in the terminal if you get your ip-address from dhcp.

Edit: What kind of network card do you have? Manufacturer etc.

---

### Post by %hMa@?b&lt;C on 2006-06-15
type "ifconfig" into terminal, post the results, I can probably help you from there

---

### Post by jasrog on 2006-06-15
My network is NVIDIA Nforce networking.

---

### Post by jasrog on 2006-06-15
What displays when I type ifconfig is this: 
eth0 Link encap: Ethernet HWADDR 00:40:CA:93:76:AC Inet6 addr:fe80:240:caff:fe 93:76ac/64 Scope:Link UP Broadcast Running Multicast MTU:1500 Metric:1 Rx packets:1822 errors 0 dropped 0 overruns 0 frame:0 tx packets 0 errors0 dropped 0 overruns 0 carrier 0 collisions 0 txqueuelen:1000 rx bytes 111598 (108.9Kib) tx bytes:0 (0.06) interrupt:217

lo Link encap:LOCAL LOOPBACK
inet addr:127.0.0.1 Mask 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
Rx Packets: 87 errors 0 dropped 0 overruns 0 frame 0 
Rx bytes:6338 (6.2kib) Tx bytes:6388 (6.2kib)

---

### Post by jasrog on 2006-06-15
Help...please so I can get online in Ubuntu.

---

### Post by %hMa@?b&lt;C on 2006-06-15
do your ISP give you a password when you first signed up? If so try 
```
sudo pppoeconf
``` also what is the name of the ISP.

---

### Post by jasrog on 2006-06-15
No password it automatically connects (always on connection).

---

### Post by jasrog on 2006-06-15
Help. Can anyone help me get online in UBUNTU?

---

### Post by Fedup on 2006-06-23
Well, there's something up with the nForce network drivers... I've just had a reinstall of Dapper and have the same problem I was having before - namely there's no network at boot. 

Disabling and reenableing from Gnome's  Admin->Networking settings gets it going again... until the next reboot when its all gone.

:-k 

](*,)

---

### Post by niteblind on 2006-06-23
In network settings is the eth0 set to use dhcp or manual? cos it looks to me as though you are only getting back IPv6 info. Are connecting to a router or straight to the cable modem?

niteblind

---

### Post by jasrog on 2006-06-25
A router now. Can you give me steps on how to setup internet network properly?

---

### Post by Apple 101 on 2006-06-25
If the internet works from another OS, say Windows, that is good.  Check the settings from there to work out how you connect to the internet.

The router should give out a DHCP IP address to your computer (if it is set to do so), otherwise you need to set static IP information.

---

### Post by pupdawg on 2006-06-28
nForce networking uses the open source driver forcedeth and nVidia provides their own driver on their web site that might work but it like most things in linux don't expect a point and click install...it can be a real pain to do something as simple and loading a driver in linux more so without a internet connection.  There are many theads on these forums relating to this same issue for help do a search for forcedeth on the forums and start reading. ;)

One thing you can try that worked for me one week and not the next was uppluging the power(wall plug) to your computer for 1 min and then booting up.  That seemed to work for awhile but now I'm thinking about buying a supported network card for linux and disabling the nForce because of all the time I waisted on this same issue. (*,)

---

### Post by nycrunner87 on 2006-06-28
I am also having internet connectivity issues. If your isp requires a username and password, how does that come into play in configuring internet access. my internet works fine in windows.

---

