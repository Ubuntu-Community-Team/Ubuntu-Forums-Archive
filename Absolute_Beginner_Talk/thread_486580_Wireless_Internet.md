---
title: "Wireless Internet"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Jexel on 2007-06-28
My internet connection on 7.04 tends to hang. I drop out at times and sometimes i can reconnect but other times i may have to log out and log back in. Other times even logging in and out don't work causing me to restart my computer. Being new to linux and all i'm sure there is an easier way than resetting my computer :P

But what I want to know is, is there a way which can prevent my internet from dropping out?

---

### Post by pyros on 2007-06-28
I wish that I had a better answer for you, but I've had this same problem for some time. In my case, it appears to be somehow related to dbus.
As a work-around, I added a launcher to my panel that runs this command in a terminal:
```

sudo /etc/init.d/dbus restart

```
whenever my internet connection drops out, I just press the launcher, and enter my password. For me, it works every time, and takes less time that disabling and enabling my internet connection. Not the right answer, I know, but it might be of some help until a fix comes through.

---

### Post by Jexel on 2007-06-28
that's good enough for me! it sure beats restarting my comp :P

i'll give it a test now

edit: it worked just fine! though to make sure it trully works i guess i have to test it out when my net actually does drop out. However, it tends to open my home folder whenver i launch it.

Thanks for the help nevertheless!

Does anyone know of the problem and perhaps have a fix they would like to share?

---

### Post by pyros on 2007-06-28
> **Jexel said:**
> that's good enough for me! it sure beats restarting my comp :P

i'll give it a test now

Yeah, it was a serious blessing when I found out about it, Wish I could remember where I read it though...

---

### Post by Jexel on 2007-06-28
hmmm...for some reason it didn't do anything whilst my internet hanged. It's really bizaare, the icon shows that I have connectivity but I can't access the internet in any way.

---

### Post by pyros on 2007-06-29
> **Jexel said:**
> hmmm...for some reason it didn't do anything whilst my internet hanged. It's really bizaare, the icon shows that I have connectivity but I can't access the internet in any way.

That's a shame. When it's having problems, can you get through to your wireless router at all? Say, by pinging the routers ip address (on my network, it's 192.168.2.1)?

---

### Post by Seisen on 2007-06-29
Jexel what is the wireless card you are using, I had problems with a dlink wireless card dropping the connection and had to use ndiswrapper and then it ran perfectly.

---

### Post by Jexel on 2007-06-29
i have a p5b-wifi motherboard so it supports wifi natively.

Can you tell me more about ndiswrapper?

---

### Post by Seisen on 2007-06-29
Type in lspci in the terminal and post the results.

---

### Post by Jexel on 2007-07-01
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4364 (rev 12)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
05:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)

---

### Post by Jexel on 2007-07-03
just installed ndiswrapper...see how it goes...

---

