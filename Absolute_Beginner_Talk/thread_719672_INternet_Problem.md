---
title: "INternet Problem"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by EffeX on 2008-03-09
Hello guys i really need help with this..

Im new to Ubuntu.. 

I load p.c up bla bla.. plug ehternet cable into back of my p.c..

How do i enable it so i can connect to the internet

THanx alot

---

### Post by jan quark on 2008-03-09
check these guides
I am not that into ethernet connections

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by EffeX on 2008-03-09
thanx.. thats well weird.. i just got a blue cable into back of p.c.

No password or nothing or card :/ weird.

---

### Post by wjston on 2008-03-09
> **EffeX said:**
> Hello guys i really need help with this..

Im new to Ubuntu.. 

I load p.c up bla bla.. plug ehternet cable into back of my p.c..

How do i enable it so i can connect to the internet

THanx alot

Welcome to the forum. First, a little more information will be useful to help you. Are you on DSL or Cable? Second, do you have a router between your pc and the modem? If you are on cable all you need to do is plug your ethernet cable into your pc and fire up Ubuntu. It should configure everything for you unless you have a router and have MAC filtering enabled. If this is a new computer and you have MAC filtering set up, you will have to add your MAC address into your router settings before you will be able to access the Internet.

---

### Post by gnuman on 2008-03-09
> **EffeX said:**
> Hello guys i really need help with this..

Im new to Ubuntu.. 

I load p.c up bla bla.. plug ehternet cable into back of my p.c..

How do i enable it so i can connect to the internet

THanx alot

Always give as much detail as possible: version of Ubuntu, PC type, and so on.

In other words, expand on the "bla bla" in your original post. :)

Usually ethernet should work just fine "out of the box" with any fairly recent Ubuntu install.

Welcome to Ubuntu.  There are zillions of us wanting to help you out. ):P

---

### Post by EffeX on 2008-03-09
ok thanx guys..


Its a cable..

32bit editon

1gb dual core... 3.0ghz p.c

Ehmmmm..

No routers or nothing.. Internet modem beside me..ethernet cable straight from modem into back of tower.. 

Any more info?? :/

and thanks alot for youre replys.. appreciated

---

### Post by wjston on 2008-03-09
> **EffeX said:**
> ok thanx guys..


Its a cable..

32bit editon

1gb dual core... 3.0ghz p.c

Ehmmmm..

No routers or nothing.. Internet modem beside me..ethernet cable straight from modem into back of tower.. 

Any more info?? :/

and thanks alot for youre replys.. appreciated

You should be able to just plug your ethernet cable into your pc, reboot, and you should have Internet enabled. If not, maybe that your NIC isn't working. Give it a try.

---

### Post by EffeX on 2008-03-09
ok i will. thanks

---

### Post by halitech on 2008-03-09
can you post the output of
```
lspci
```
and 
```
ifconfig
```

---

### Post by EffeX on 2008-03-09
this what happend..

PLug internet cable in.

Reboot pc up


and i hover my mouse over top right corner thing and its got "!" over it

saying .. No network connections..

---

### Post by halitech on 2008-03-09
so either it isn't connecting to your modem or your card isn't being seen. did you run those commands from my previous post?

---

### Post by EffeX on 2008-03-09
what do u mean... how do i do commands?

---

### Post by halitech on 2008-03-09
Applications - Accessories - Terminal

```
lspci
```

and

```
ifconfig
```

---

### Post by EffeX on 2008-03-09
lspci it says

Intel co-operating 82945G/GZ/P/PL memory controller Hub (rev 02)


ifconfig:

link encamp ; local loopback
int addr: 127.0.0.1 mask: 255.0.0
inet6 adrr: 1/128 scope:host
UP PLAYBAC RUNNING MTU:16436 metric@1
RX pacjkets:48 errors:0 dropped:0 overruns:0 frame:0
TX packets:48 erros:0 dropped:0 overruns :0 carrier :0
Collisions :0 txquelen:0;
Rx bytes:3568 (3.2kb) TX bytes 3568 (3.4)kb

---

### Post by diablo75 on 2008-03-09
Type in:

```
ifconfig eth0 up
```

And then...

```
dhcpcd eth0
```

Then....

```
ifconfig
```

and paste the output for all of the above in here.  Thanks.

---

### Post by halitech on 2008-03-09
> **EffeX said:**
> lspci it says

Intel co-operating 82945G/GZ/P/PL memory controller Hub (rev 02)

I'm going to guess there was alot more there then just that. Mine looks likes this:

```

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
02:0a.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
02:0b.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
02:0c.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)


```


> 
ifconfig:

link encamp ; local loopback
int addr: 127.0.0.1 mask: 255.0.0
inet6 adrr: 1/128 scope:host
UP PLAYBAC RUNNING MTU:16436 metric@1
RX pacjkets:48 errors:0 dropped:0 overruns:0 frame:0
TX packets:48 erros:0 dropped:0 overruns :0 carrier :0
Collisions :0 txquelen:0;
Rx bytes:3568 (3.2kb) TX bytes 3568 (3.4)kb

basically the system doesn't know you have a network card or its not configured properly

---

### Post by prshah on 2008-03-09
> **EffeX said:**
> ok thanx guys..

No routers or nothing.. Internet modem beside me..ethernet cable straight from modem into back of tower.. 



Are you sure it's an Ethernet cable and not a USB cable?

Switch on your modem, then open Applications-Accessories-Terminal and type in the command "sudo mii-tool" and paste the results here.

Cheers,
PRShah

---

### Post by EffeX on 2008-03-09
this is weird tbh and spinning me out lol..

not good with pc's

---

### Post by halitech on 2008-03-09
I know it seems like you are speaking another language (which in fact you are) but you need to help us help you. could you post all of the output of lspci? I think what you did post was something other then your network card.

---

### Post by prshah on 2008-03-10
> **EffeX said:**
> this is weird tbh and spinning me out lol..

not good with pc's

I dont think you have an Ethernet connection at all. It is most likely USB. An easier way to check: Switch on your modem, wait 5 mins, then tell us what lights are available in the modem and what is their status: (solid on, solid off, blinking, flickering [very fast blinking], etc)

Also include any brand names and a picture if possible. Who is your ISP (Internet Service Provider)?

Cheers,
PRShah

---

### Post by EffeX on 2008-03-10
ehm my Isp is Ntl.. now Virgin media..

---

### Post by wjston on 2008-03-10
> **EffeX said:**
> ehm my Isp is Ntl.. now Virgin media..

Maybe you should just quit with all the acronyms and say what you mean. I think it would be much easier to diagnose and remedy your situation.

---

### Post by prshah on 2008-03-11
> **EffeX said:**
> ehm my Isp is Ntl.. now Virgin media..

What about the lights.. and a picture?

Cheers,
PRShah

---

### Post by EffeX on 2008-03-26
i got a BLUE cable. with ETHERNET written on it..

---

