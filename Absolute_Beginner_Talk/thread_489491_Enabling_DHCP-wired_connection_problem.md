---
title: "Enabling DHCP-wired connection problem"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by shoutroom on 2007-07-01
Hi guys..
After scanning through dozens of threads throughout the forums, I practiced a number of techniques in fixing my dual booted computer's wired internet. (My vista section works but my Ubuntu doesn't).

After typing in ipconfig in my CMD in windows, I guess I have the problem, but I don't know how to fix it.
It's probably the fact that DHCP is disabled so that the Ubuntu OS can't detect it when trying to connect to the internet as this is what's returned after typing "ipconfig/all" in my CMD in vista:

```

Broadband connection
DHCP Enabled:No
Autoconfiguration Enabled:Yes
IPv4 Address:219.77.19.90<Preferred>
Subnet Mask:255.255.255.255
Default Gateway:0.0.0.0
DNS Servers:218.102.62.71,205.252.144.126
NetBIOS over Tcpip:Disabled

```
Other info is local area and I suppose it's not needed.

Can someone please tell me how to enable my DHCP as I am a complete newb in Linux. Or if I have a misconception to what is returned from the CMD, correct me to the path so that I will be able to operate my internet connection.

Thx, all help appreciated

---

### Post by cogadh on 2007-07-01
Go to Sytem > Adminstration > Network, choose your connection, click on Properties, change the configuration to Automatic.

---

### Post by shoutroom on 2007-07-01
The connection is already set to automatic.

---

### Post by cogadh on 2007-07-01
Does your router allow DHCP conections?

---

### Post by shoutroom on 2007-07-01
forgot to mention this, im using a modem.
and analyzing what's returned from the CMD, seemingly no.

---

### Post by mendingo84 on 2007-07-01
are you sure you get your IP from a DHCP server ? isn't it static?

---

### Post by shoutroom on 2007-07-01
i tried putting my ip in for the static ip option, but no msg popped up after all the modifications. and i didnknow how to connect to the internet.

---

### Post by cogadh on 2007-07-01
> **shoutroom said:**
> forgot to mention this, im using a modem.
and analyzing what's returned from the CMD, seemingly no.
I'm assuming you mean a cable or DSL modem, in which case you should check with you ISP for the proper configuration and use the same network tool to apply that configuration.

---

### Post by shoutroom on 2007-07-01
> **cogadh said:**
> I'm assuming you mean a cable or DSL modem, in which case you should check with you ISP for the proper configuration and use the same network tool to apply that configuration.

how can I check my ISP?

---

### Post by cogadh on 2007-07-01
Contact the tech support or visit the website for your ***I***nternet ***S***ervice ***P***rovider, they need to tell you what your proper network configuration should be.

---

### Post by shoutroom on 2007-07-02
Okay...I contacted the tech support of my ISP.
They told me that I have a dynamic IP address, thus I will not be able to use the "static IP" option.
I was also notified that I'm currently running an ADSL modem.

If this is of any use, it's a picture cut from a screenshot with the ipconfig/all information of my ISP (PPP adapter Broadband connection) in it:
[IMG]http://statistic.wmn.cc/picture.jpg[/IMG]

As for the configuration stuff...my ISP said they only offer technical support for windows related issues.

---

### Post by shoutroom on 2007-07-02
Btw, I'm running a "NEC NTA-3110" modem, if that's of any use.

---

### Post by shoutroom on 2007-07-02
Do I need to check for my modem's chipset?

---

### Post by Seisen on 2007-07-02
What does it say in Ubuntu when you put this in the terminal and what is the network card you are using in Ubuntu.

```
ifconfig
```

---

### Post by cogadh on 2007-07-02
I don't know much about this (I have a cable connection), but since your ISP says you have a PPP connection, you probably need to run pppoeconf to configure the PPP connection. Someone else will have to give you the specifics, but to start the configuration, all you have to do is run ```
sudo pppoeconf
```
After that, it should just be a simple matter of entering the PPP Adapter connection info you posted above. Again, I've never done this before, so if I'm wrong, hopefully one of the brainiacs here will correct me.

---

### Post by shoutroom on 2007-07-02
@cogadh,  I processed "sudo pppoeconf" in the terminal, and I was returned with a password prompt. Since I normally need to type in a password and username when accessing internet using my vista OS on the same computer, I assume that we're on the right track. However, the password prompt didn't output any keys onto the terminal when I typed in my password. And when I pressed enter, the terminal just created a new line.

@Seisen,here is the ifconfig:
```

eth0               Link recap:Ethernet HWaddr 00:1A:92:26:18:F4
                      inet 6 addr:fe80::219:92ff:fe26:18f4/64 scope:link
                      UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
                      RX packets:3 errors:0 dropped:0 overruns:0 frame:0
                      TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
                       collisions:0 txqueuelen:1000
                       RX bytes:748(748.06) TX Bytes:9394 (9.1Kib)

eth0:avah      Link  encap:Ethernet HWaddr 00:1A:92:26:18:F4
                       inet addr:169.254.6.213 Bcast:169.254.255.255 Mask:255.255.0.0
                       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

lo                    Link encap:Local Loopback
                       inet addr:127.0.0.1 Mask:255.0.0.0
                       inet6 addr:::1/128 scope:host
                       UP LOOPBACK RUNNING MTU:16436 Metric:1
                       RX Packets:32 errors:0 dropped:0 overruns:0 frame:0
                       TX Packets:32 errors:0 dropped:0 overruns:0 carrier:0
                       collisions:0 txqueuelen:0
                        RX bytes:2671(2.6KiB) TX bytes: 2671(2.6KiB)

```

---

### Post by cogadh on 2007-07-02
It was asking for your Ubuntu login password, which will give you the necessary administrator-like permissions to configure your internet connection. The pppoeconf command is not a command to launch your internet connection, it is a command to configure the necessary connection in order for you to get on the internet.

---

### Post by shoutroom on 2007-07-02
Wow, thankyou so much!
I accessed the internet after following a wizard which was prompted when I typed in "sudo pppoeconf" with permissions allowed.:popcorn:

---

