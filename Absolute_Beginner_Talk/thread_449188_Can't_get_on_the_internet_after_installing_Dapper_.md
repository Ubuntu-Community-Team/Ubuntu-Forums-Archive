---
title: "Can't get on the internet after installing Dapper Drake"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by childofGod on 2007-05-20
I installed Dapper Drake because that's the install disk I had available to me.  I can't get on the internet with that machine so I'm posting from a Windows PC at the moment.  The motherboard is a Gigabyte Technology GA-M55plus-S3G.  The CPU is an AMD Socket AM2 Athlon 64 3800.  The Chipset is nVidia GeForce 6100 Northbridge and nVidia nForce 430 Southbridge.  It has an onboard Realtek ALC883 CODEC chip, which worked immediately upon installation of dapper:D  The LAN is a Marvell 88E1116 phy (10/100/1000Mbit).  This shows as etho and is activated as DHCP automatically upon installation of dapper.  It will not get on the internet:(  I tried configuring it as static to no avail.  I read a post somewhere in hear which lead me to try sudo pppoeconf but also to no avail:(  I am using a Westell Versalink dsl router configured for PPPOE.  Any help will be appreciated.  Is there any other information I need to post to get to the proper solution.

---

### Post by Bachstelze on 2007-05-20
What if you run DHCP manually ?

```
sudo dhclient eth0
```

---

### Post by dilb on 2007-05-20
Just a though, are you able to connect to any sites at all? When I first installed linux, I could only connect to a handful of websites. I eventually tracked it down to a setting in Firefox to do with IPv4/6.

I suspect this is not the answer to your problem, but you may want to give it a quick try. Open firefox, type about:config in the address bar (and hit return), Filter for IPv6 and switch the 'DisableIPv6' setting.

If this doesn't work, switch back, and ask for more help!

---

### Post by childofGod on 2007-05-20
Thanks, but that didn't work.

---

### Post by childofGod on 2007-05-20
> **HymnToLife said:**
> What if you run DHCP manually ?

```
sudo dhclient eth0
```
Unfortunately manual dhcp configuration didn't do the trick either.

---

