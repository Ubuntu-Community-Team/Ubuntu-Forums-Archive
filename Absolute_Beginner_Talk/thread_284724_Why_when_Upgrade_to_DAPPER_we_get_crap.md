---
title: "Why when Upgrade to DAPPER we get crap"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-10-26
](*,) 

I upgraded to dapper from Breezy and now I have lost functionality.

Why is new and improved  less  than what I had before upgrade?

Hear is the story - I upgraded to dapper I finally got my wifi card working so when the updates came down I installed them ok.

Now after the updates I lost my wifi connection. It does not show up in system > networking so I cant configure it. This is after installed updates to dapper.](*,) 

Thats not bad enough I use to have small grafts on my panels to show networking,cpu, and disk activity from the System Monitor. That not available in the new and improved Dapper .  WHY ](*,)

---

### Post by TrueJk7 on 2006-10-26
Well #1 if you are looking for assitance you need to provide technical data so we on the forum can help you out.

I had the same problem with the Belkin 54g 7010 wireless card. Is that the same card? and what do you get from the commands
```
ifconfig
iwconfig
```

Do you use ndiswrapper? Hope to help but we need the data

---

### Post by kent41 on 2006-10-26
> **TrueJk7 said:**
> Well #1 if you are looking for assitance you need to provide technical data so we on the forum can help you out.

I had the same problem with the Belkin 54g 7010 wireless card. Is that the same card? and what do you get from the commands
```
ifconfig
iwconfig
```

Do you use ndiswrapper? Hope to help but we need the data

My card is a Dlink DWL-G630
```

kent@kent-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```
```

kent@kent-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:57:E4:34
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe57:e434/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:168781 (164.8 KiB)  TX bytes:45154 (44.0 KiB)
          Interrupt:217 Base address:0x6800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)
```

---

### Post by kent41 on 2006-10-26
as you can see the wireless does not show up after the updates.

No I did not have to use ndiswrapper before the updates.

---

### Post by Arevos on 2006-10-26
Some quick googling reveals [this webpage](http://www.neowin.net/forum/index.php?showtopic=453699), helpfully titled "Howto: Ubuntu Dapper and Wireless home network, Specifically DWL-G630 D (Atheros chip)"

---

### Post by kent41 on 2006-10-26
> **Arevos said:**
> Some quick googling reveals [this webpage](http://www.neowin.net/forum/index.php?showtopic=453699), helpfully titled "Howto: Ubuntu Dapper and Wireless home network, Specifically DWL-G630 D (Atheros chip)"

Thanks for the reply but that situation was his cpu was unable to recognize
the Dlink card, my computer sees my  card under Dapper before I added the updates.

I think it is a problem with the updates made to Dapper can I back out the updates to Dapper? and get my wifi back

---

### Post by felixq78 on 2008-01-11
[QUOTE=TrueJk7;1664880]Well #1 if you are looking for assitance you need to provide technical data so we on the forum can help you out.

ITechnical data ? What's the point ? Before the upgrade Ubuntu was relatively user friendly.
Now it's just a pile of crap.
Not everyone wants  to waste endless hours re-building their OS, some people actually need their computer to operate from scratch. We just don't have the time to play around.
Computers are a tool which is supposed to make our work quicker and easier.
It's like buying a car only to discover that the engine and transmission are compatible and you have to install a new bell housing so they fit together.
What a joke!
Ubuntu used to be OK, now it's just another useless half baked Linux OS.

---

### Post by Amstell on 2008-01-11
> **felixq78 said:**
> [QUOTE=TrueJk7;1664880]
Ubuntu used to be OK, now it's just another useless half baked Linux OS.

I think ubuntu has come a very long way since I first started using dapper.  Currently on Gutsy and looking forward to Heron I think they are doing a great job.  Maybe its operator error?

---

### Post by thelatinist on 2008-01-11
> **Amstell said:**
> [QUOTE=felixq78;4116396]

I think ubuntu has come a very long way since I first started using dapper.  Currently on Gutsy and looking forward to Heron I think they are doing a great job.  Maybe its operator error?

Personally, I would check the nut holding the mouse.

---

