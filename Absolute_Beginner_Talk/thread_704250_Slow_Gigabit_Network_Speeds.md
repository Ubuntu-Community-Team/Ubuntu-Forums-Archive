---
title: "Slow Gigabit Network Speeds"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by webjames on 2008-02-22
Hello, 
I have a laptop (ThinkPad T41) connected at 1000 Mb/s with a gigabit switch to my desktop with hardware raid, with a gigabit network card in, connected at 1000 Mb/s. However when copying file i get a maximum of 6 -9 mb/s with it averaging around 3. This is really poor for a gigabit network. What is causing this?

I am happy to do any number of tests and give any information regarding anything helpful to discovering the cause of this problem.

Many thanks!

---

### Post by Mithrilhall on 2008-02-22
```

apt-get install ethtool net-tools

mii-tool

```

This should show what your network card is set to. These tools will also let you change the settings.

The other thing I would do is install Wireshark and iftop and watch your traffic; just check out what's going on and see if you notice anything out of the ordinary.

If it's a managed switch I would check the interfaces for errors.

---

### Post by njparton on 2008-02-22
Are you using Cat5E (at least) or Cat6 cabling?

Is the switch jumbo frame capable?  If so set the relevant mtu size via your interfaces file.

---

### Post by webjames on 2008-02-22
Hi, thanks for your replies guys, i have run the mii-tool and it seems my network was set to 100base not 1000 as shown in the connection information under the network manager. Is this a bug?
> 
james@james-desktop:~$ sudo mii-tool
eth0: no link
eth1: negotiated 100baseTx-FD flow-control, link ok

I am using a 3com switch (3com gigabit switch8), with Cat6 cabling.

Thanks,

EDIT: my switch does support jumbo frames up to 9k. How can i enable 1000mb/s and set the interface file? I have just run:
> james@james-desktop:~$ sudo ethtool eth1
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes


That states that the speed is 1000. What is going on? Which tool should i believe?

---

### Post by webjames on 2008-02-22
Hi, just installed wireshark, nothing out of the ordinary.

Here is some more information about my network hardware and software:

Router
Hardware: Buffalo WHR-G54S
Firmware: Tomato 1.16

Switch: 3com Gigabit Switch 8

Cabling: All Cat6

Laptop and Desktop running Ubuntu.
PS3 gets media streamed via MediaTomb
Other computers connect via wireless via the router.

192.168.1.110	james-desktop
192.168.1.113	james-ubuntu-laptop-wired
192.168.1.118	ps3
192.168.1.133	james-ubuntu-laptop

Obviously when running the speed test my laptop was wired into the network. I wonder if i would be better of running DD-WRT? although i doubt the router is anything to do with the problem as everything wired connects via the switch detailed above.

Thanks,

---

### Post by Mithrilhall on 2008-02-22
Try setting both sides to 1GB Full Duplex and turn off auto-negotiation.

Something like...

ethtool -s eth1 autoneg off speed 1000 duplex full

---

### Post by njparton on 2008-02-22
add the following line to your "/etc/network/interfaces" file in the relevant section for your eth0 NIC:

```
mtu 9000
```

then reboot or restart networking

---

### Post by webjames on 2008-02-22
Thanks for you replies,
I have now set the MTU to 9000 however i am still getting slow speeds, and unusual activity, i have included a screenshot of the problem:

as you can see the transfer peaks around 13mbs, but constantly dips like 13-0-13-0-13-0...

this is between my laptop and ps3. both gigabit enabled.

EDIT: 
I have changed the MTU however this interrupts the network manager, i sometimes use a wifi network. How can i change the default from 1500 to 9000.

---

### Post by webjames on 2008-02-24
**SOLUTION:**
I compiled the new e1000 module from [http://sourceforge.net/projects/e1000/](http://sourceforge.net/projects/e1000/)
just remember to:
> sudo rmmod e1000

Then compile and install the e1000 module then:
> sudo modprobe e1000

I also manually configured my network interface to set the correct mtu: (for me 9000)
This will temporarily set the mtu, just see if it accepts the mtu you are trying, i know some drivers are limited to 7000.
> 
sudo ifconfig eth0 mtu 9000
Next lets set it so it will be set everytime you boot up:
> sudo nano /etc/network/interfaces
This is what my file looks like i added the eth0 bit:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
up ifconfig eth0 mtu 9000
```
Now press ctrl+x press y to save changes and enter.
Then all is left to do is restart the network:
> sudo /etc/init.d/networking restart
Type > ifconfig to see if it has worked.

---

### Post by webjames on 2008-02-24
**UPDATE:**
The previous post did work, and has set my mtu. however i am still experiancing the pulsing and slow speeds.

The screen shot shows what i am talking about: 
The high speed activity it over HTTP and the lower speed is over samba (SMB) as you can see both signals are pulsing. Although setting the correct MTU _has_ speed things up it still hasn't solved the pulsing problem. compiling the latest driver doesn't seem to do anything.

there is now a launchpad bug:

[https://bugs.launchpad.net/ubuntu/+bug/194832](https://bugs.launchpad.net/ubuntu/+bug/194832)

---

### Post by carverj on 2008-02-24
> Router
Hardware: Buffalo WHR-G54S
Firmware: Tomato 1.16

Switch: 3com Gigabit Switch 8

Cabling: All Cat6

Laptop and Desktop running Ubuntu.
PS3 gets media streamed via MediaTomb
Other computers connect via wireless via the router.

192.168.1.110 james-desktop
192.168.1.113 james-ubuntu-laptop-wired
192.168.1.118 ps3
192.168.1.133 james-ubuntu-laptop

So you have definately isolated this performance dip with relation to the workstation and the laptop (wired) through the gigabit switch. The cat6 cabling is fine.....
the mtu is set and happily configured...
you have rebooted.....
are you dual booting these machines?
in other words, does this dip happen only with ubuntu?

---

### Post by webjames on 2008-02-24
I have manually configured my network, all linking components are less than a month old. my laptop and desktop both run ubuntu linux.
I do dual boot my desktop with windows 2000, but haven't booted that for years.

i have run all tests between laptop and desktop. here is a copy of the screen shots of both my desktop and laptop activity when copying a file from my desktop to my laptop, then back again:

---

### Post by sternkanz on 2008-02-26
Ok, so I'm having a similar problem. 3 machines, 1 PC WinXP, 1 laptop WinXP, and one laptop Gutsy. The two WinXPs are connected by cat5 to a 100Mbps adsl2 modem. The Gutsy laptop is connected by wireless to a linksys modem, which is connected by cat5 to the adsl modem. 

The problem: I'm getting absolutely horrible transfer speeds from my Gutsy laptop to the other two machines. And I mean absolutely horrible. Right now I'm attempting to copy a 3.7GB iso file from it to my WinXP PC and its estimating at about 4 hours. I've tried running the mii-tool thing that some people seem to talk about and this is what I get:

stern@stern-laptop:~$ sudo mii-tool
eth0: no link
SIOCGMIIPHY on 'eth1' failed: Operation not supported
stern@stern-laptop:~$ sudo ethtool eth1
Settings for eth1:
        Link detected: yes

and that's all I get. Can anybody help me? I used to have WinXP installed on this laptop and I never had any transfer issues.

**Edit: Might want to move this to networking..?**

---

### Post by SkidShot on 2008-02-26
> **Mithrilhall said:**
> Try setting both sides to 1GB Full Duplex and turn off auto-negotiation.

Something like...

ethtool -s eth1 autoneg off speed 1000 duplex full

Mithrilhall probably gives the solution here. 
I don't know if you tried it already but you might want to look into that if you already haven't.
From my experience as a network engineer 9 out of 10 times the problem you describe (avg throughput 2-4 Mbps, max 8-9Mbps) is related to a duplex mismatch.

Please try it (again) with both sides set to the same fixed settings.
If that works out, you could either try to switch BOTH sides to auto negotiation again (as that is the best practise for 1Gbps ethernet) or just leave it that way.  :)

---

### Post by sternkanz on 2008-02-27
stern@stern-laptop:~$ sudo ethtool -s eth1 autoneg off speed 1000 duplex full
Cannot get current device settings: Operation not supported
  not setting speed
  not setting duplex
  not setting autoneg

---

### Post by sternkanz on 2008-03-13
bump? :)

---

### Post by jedi-penguin on 2008-05-04
Have you try to edit the first line of the /etc/hosts file? I hear there were a bug in there.

127.0.0.1  localhost  <your hostname>

---

### Post by sot3 on 2008-05-13
Sternkanz - are you sure you have an eth1 interface?

Try ifconfig -a to list them.  You should see lo0 and another...perhaps eth0?

---

