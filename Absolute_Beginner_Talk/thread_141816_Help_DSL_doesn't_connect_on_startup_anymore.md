---
title: "Help: DSL doesn't connect on startup anymore"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by Jucato on 2006-03-09
... and it always did, well until this morning.
I'm not that knowledgeable about networks, internet, pppoe, etc. so I'm really pulling my hair here.

Here's the situation: when I installed/reinstalled Ubuntu, I'm always able to connect to the internet through my DSL (it has a router, if that's what you call the modem-like box thingy) just by using
```
sudo pppoeconf
```
I set it up so that it would connect on start up (since Kubuntu doesn't have a GUI for PPPoE). It has been working perfectly for the past month. But when I woke up this morning, it didn't connect automatically anymore. Worse, just typing ```
pon dsl-provider
``` doesn't connect me to the net. I have to do pppoeconf again, every time I restart the pc.

I don't even know where to start investigating, what log files to look at, what things to check, what to post so that you guys could diagnose. The only thing I did last night was to change my hostname from "hinotori" to "firebird" and back to "hinotori" again, using KDE's Network Settings GUI. I'm not sure if that had anything to do with this.

Please I need help... I'm really getting a bit flustered here... on the verge of panicking... :cry:

---

### Post by meborc on 2006-03-09
i had the same problem when not shutting down correctly... that means all hard-reboots, powerlosses etc forced me to make the conf again...

but i never had the problem when normally shutting down - booting...

---

### Post by Jucato on 2006-03-09
*gulp* I hope this isn't a very unique and isolated case. It will be so much harder to find help if that's the case... :cry:

---

### Post by Jucato on 2006-03-09
Just wanted to add some info, hoping somebody could help.

When I run "pon dsl-provider" after startup, I get these in my system logs:
```
pppd[8900]: Plugin rp-pppoe.so loaded.
pppd[8902]: pppd 2.4.3 started by fenyx, uid 1000
pppd[8902]: sendPacket: send: Network is down
pppd[8902]: Exit.
```

Then I had an idea to compare today's system logs to the system log last week. I compared everything, line by line, from boot up to the time I log in to KDM. I found that these two lines are missing from today's logs:

```
localhost kernel: [4294700.341000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
localhost kernel: [4294700.520000] NET: Registered protocol family 24
```

I guess those two lines (present in last week's log) showed that my system connect during startup. Now they are missing, and I have no idea what to do. I'm still able to connect to the internet, but, like I've said, I must run pppoeconf everytime. 

I hope someone out there has an idea what to do.

this is the result of running ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:14:2A:0E:5B:76
          inet6 addr: fe80::214:2aff:fe0e:5b76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172874 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:98116746 (93.5 MiB)  TX bytes:63442404 (60.5 MiB)
          Interrupt:23 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22708 (22.1 KiB)  TX bytes:22708 (22.1 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:58.69.16.1  P-t-P:210.5.96.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:172746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194327 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:94200492 (89.8 MiB)  TX bytes:59162865 (56.4 MiB)
```

---

### Post by droazen on 2006-03-12
I had a similar problem with having to run pppoeconfig after every boot. The solution turned out to be editing the /etc/network/interfaces file so that the "auto eth0" stanza came before the "auto dsl-provider" stanza. For example, 

```

auto eth0
iface eth0 inet dhcp
pre-up /sbin/ifconfig eth0 up

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider
```

I think the problem was that during boot, ifup -a brings the interfaces named in the "auto" stanzas in /etc/network/interfaces up *in the order they appear in the file.* So it makes sense that eth0 should be brought up first.

I hope this works for you!

---

### Post by Jucato on 2006-03-13
It didn't work.

BUT!!! You led me to the answer, and now everything works again!!!!!!!
Thank you so much!!! :D

The answer to all my troubles was in fact found in the /etc/network/interfaces file. 
I tried to do a manual ifup -a and it kept on saying that I don't have the variables for eth0/inet. Checking on the interfaces file, I discovered that I had "iface eth0 inet static", which would mean that I needed to enter an IP address and netmask. But my ISP doesn't give those out.
But changing it to "iface eth0 inet dhcp" caused the boot up process to slow down more than usual (at the networking part). What I did was I commented out that whole auth eth0 section and ran pppoeconf again. And guess what? The line should have been "iface eth0 inet **manual**"!!  Now it works as it did before.

Thank you thank you thank you!!! \\:D/

---

