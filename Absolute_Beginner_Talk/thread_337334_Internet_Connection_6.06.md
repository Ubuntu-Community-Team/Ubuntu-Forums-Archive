---
title: "Internet Connection 6.06"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by azurehi on 2007-01-12
Just got 6.06 cd and have only explored from live cd.  I cannot figure out how to establish my internet connection - I have dsl from Qwest/msn (colorado, usa) but cannot get support for any linux.  I have the IP numbers, etc. but cannot understand which options to choose in the two network options in Ubuntu.  Can't connect w/Firefox or settings from Outlook Express.  Any suggestions?  Detailed instructions?  I/m assuming that connection to the internet can be made from the cd, without actually installing Ubuntu at this point.  Thanks.:???:

---

### Post by jas0 on 2007-01-12
I'm assuming you have the following setup:

[INDENT]**Internet < DSL modem > Your Computer**[/INDENT]

Open a terminal window and type: 

```
ifconfig
```

Tell us whether you see an interface called "eth0." if you don't, try typing:

```
ifconfig eth0 up
ifconfig eth0 <--- do you see it now?
dhcpcd eth0
```

And try browsing again.

---

### Post by Iowan on 2007-01-12
I need to upgrade from dialup, so talked to a Qwest sales rep about Qwest DSL.  She told me my Linux workstation (and Linux router) would not work with MSN, (but I could sign up with Qwest.com as ISP instead).  I'm hoping she (and the collegue with whom she conferred) was wrong - but I haven't signed up yet. I'll be anxious to see you make it work!

---

### Post by azurehi on 2007-01-13
> **Iowan said:**
> I need to upgrade from dialup, so talked to a Qwest sales rep about Qwest DSL.  She told me my Linux workstation (and Linux router) would not work with MSN, (but I could sign up with Qwest.com as ISP instead).  I'm hoping she (and the collegue with whom she conferred) was wrong - but I haven't signed up yet. I'll be anxious to see you make it work!
I just contacted Qwest technical support and was told that Qwest techs are not trained to offer support in setting up DSL connectivity to Linux; she checked with someone and assured me, however, that Qwest DSL can be setup in Linux.  I will post back as I try to setup in Ubuntu, probably 6.06.

---

### Post by azurehi on 2007-01-13
> **jas0 said:**
> I'm assuming you have the following setup:

[INDENT]**Internet < DSL modem > Your Computer**[/INDENT]

Open a terminal window and type: 

```
ifconfig
```

Tell us whether you see an interface called "eth0." if you don't, try typing:

```
ifconfig eth0 up
ifconfig eth0 <--- do you see it now?
dhcpcd eth0
```

And try browsing again.

I am working from the live cd, 6.06, and not installed ubuntu.  I did not see the setup you describe.  Somehow I found "terminal", typed in ifconfig, saw eth0; typed in the other commands, at one point saw "permission denied".  I went to Network Tools and Network Settings":  in tools saw loopback interface (lo); in Settings, saw interface eth0 is active; host settings:  host name  ubuntu, domain name  blank; DNS servers 192.168.0.1 and 205.171.3.65 (same as DNS info from Qwest); Search Domains  domain.actdsltmp.  in firefox search and url entry, e.g., yahoo.com, produce no results.  On my dsl modem, the internet/ethernet lights remain steady - they flicker when I search form firefox on my windows xp OS.  
Is working from a live cd and not an installation a factor?  Qwest dsl will not help - windows, mac only.  I was hoping that a step-by-step guide was available online somewhere.  Perhaps I am just too unskilled in setup to use ubuntu, maybe other linux distros.  Anyway, I appreciate your help thus far and am open to any suggestions.  I believe strongly in what ubuntu stands for and open source in general.  Thanks.

---

### Post by azurehi on 2007-03-01
Problem Solved (in 6.10, at least).  Disabled ipv6 by typing about:config in firefox; in filter box typed ipv6, R-clicked value and toggled to other setting, i.e., false to true.  I did this after installing 6.10 but it works to solve this problem in other distros.  Discovered this suggestion by search and resubmitting question - thanks to all.  :)

---

