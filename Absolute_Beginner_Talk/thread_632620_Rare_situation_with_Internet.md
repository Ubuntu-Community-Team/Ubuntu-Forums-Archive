---
title: "Rare situation with Internet"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by deboare on 2007-12-05
Hi everyone,
I'm new to the forums and to Ubunto, so as my status says it: this is my first cup of Ubuntu. I'm Brecht Debaere and live in Belgium, I'm 16 years old and would have Ubunto on my own computer if I wouldn't play DirectX games ^^. Anyhow, I've installed Ubuntu on my stephfather's PC hoping it would solve his problems he was experiencing with Windows. He was always complaining about how slow his computer was and how it would keep on slowing trough the years. Then when I googled I found this site: whylinuxisbetter; almost everything I know from Linux uptil now I got from that site :). After installing I experienced some troubles however with connecting to the internet.
We do not have a static IP so basically everything should just work (self detect). I've tried some solutions in some threads here; like deleting some lines for loading drivers who might be in conflict with eachother or the device; this did not seem to work however.
The weird thing is; before Ubuntu the internet started to get weird too. I needed to open some ports so I pressed the reset button; this was the point where the router started to trip. The status-light did not flash anymore. I believe that this still cannot be the issue because when I use the same cable for my stephfather's PC, so I take the cable from his laptop and put it in my computer; I have internet (I work with XP). So the issue cannot be the cable itself nor the router.
Then what is?
Network Card: Realtek RTL-8139/8139C/8139C+
I've tried disabling IPv6 in Firefox, other cable, deleting the "cp" driver line, deleting the "too" driver line. Also the weird thing is; I'm receiving bytes, however I'm not sending them unless I try to ping to google say for instance. But when I ping I get no response.

Please help ^^
Thanks

---

### Post by Jonne on 2007-12-05
what's the output of ifconfig? (run ifconfig in a terminal)

---

### Post by deboare on 2007-12-05
I cannot access my stephfather's computer right now; but I can recall that it had:
"Cannot find IPv6 router" in it, even when I disconnected the router and inserted the cable directly into the modem...

Thanks for the response
Deboare

---

### Post by deboare on 2007-12-06
Okay I got access to his PC again and ran ifconfig in the Terminal screen. Going to copy the output of it to this post:
```

quiny@Laptop:~$ ifconfig
eth0
Link encap:Ethernet  HWaddr 00:0F:B0:6F:59:C0
inet6 addr: fe80::20f:b0ff:fe6f:59c0/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:415 errors:0 dropped:0 overruns:0 frame:0
TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:24900 (24.3 KB)  TX bytes:5153 (5.0 KB)
Interrupt:20 Base address:0x4400

eth0:avah
Link encap:Ethernet  HWaddr 00:0F:B0:6F:59:C0
inet addr:169.254.7.255  Bcast:169.254.255.255  Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
Interrupt:20 Base address:0x4400

lo
Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:16 errors:0 dropped:0 overruns:0 frame:0
TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
collissions:0 txqueuelen:0
RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

```

Hope you guys can help me with this issue further,
thanks.
Deboare

---

### Post by deboare on 2007-12-06
Bump

---

### Post by deboare on 2007-12-07
Bump again ^^

---

### Post by Jonne on 2007-12-07
In system>administration>network , try playing with the settings (set it to DHCP and roaming mode, see if one of those work). It seems like the problem is that it tries to use ipv6 instead of ipv4. I've never seen that happen, really.

---

### Post by deboare on 2007-12-07
> **Jonne said:**
> In system>administration>network , try playing with the settings (set it to DHCP and roaming mode, see if one of those work). It seems like the problem is that it tries to use ipv6 instead of ipv4. I've never seen that happen, really.

Thanks for your reply Jonne,
I'm trying different settings out now.
Anyhow I thought IPv6 replaced IPv4? So shouldn't it be using the new one? Don't blame me for my n00bness.

Deboare

---

### Post by deboare on 2007-12-07
I've tried the two settings found in Network Settings => Properties: DHCP and IPv4ll yet none of them makes my internet work. We do not have a Static IP so I cannot pick that option.
Could it be that the problem is with the driver active on the device?

Deboare

---

### Post by fourscore on 2007-12-07
Are you dual booting  with  WinXP and Ubuntu.     There is an issue with Realtek Ethernet card when dual booting with Windows and Linux. Pls refer to the flwg link - [http://ubuntuforums.org/showthread.php?p=3446114](http://ubuntuforums.org/showthread.php?p=3446114)

---

### Post by deboare on 2007-12-07
I wish it was that easy. However I am not dual booting. Windows has been removed completely.
I tried the tip in this thread: [http://ubuntuforums.org/showthread.php?t=169633](http://ubuntuforums.org/showthread.php?t=169633), well not really I just removed the cp driver line in modules.dep in the lib folder...
Anyhow, the internet still doesn't seem to work :|

Deboare

---

### Post by deboare on 2007-12-07
I'll describe the situation as it goes exactly, hopefully that will give you guys a bit more info to work with. What I have already done is this:
removed the "8139cp" driver line from the modules.dep in the lib folder

What I do is this:
I start up
I put in the cable with internet (now directly from the modem, in the beginning of the thread I was still using a router, because the router was a bit ****** up I am now just taking the cable straight from the modem)
Then I wait for the "Requesting network adress" to get finished.
So now the internet should work right?
I open Firefox, no internet
I check the Connection Information and this is what it gives me:
Interface: Wired Ethernet (eth0)
Driver: 8139too
IP Adress: 0.0.0.0
Broadcast Adress: 0.0.0.0
Subnet Mask: 0.0.0.0
Default Route: 0.0.0.0
Primary DNS: 0.0.0.0
Secondary DNS: 0.0.0.0
Hardware Adress: 00:0F:B0:6F:59:C0

I'm supposed to get an IP but I ain't getting one, please help me on this issue.
Thanks ^^
Deboare

---

### Post by deboare on 2007-12-07
Lol, while I tried everything and looked and played with every setting. I thought it were the drivers and stuff while anyway it was the modem itself. All I had to do was restart it and BAM the internet worked on the laptop.
What I do not understand about this is why did my desktop computer's internet work?
Maybe if anyone can clarify this for me I would understand this issue better...
Thanks ^^
Deboare

---

