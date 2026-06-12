---
title: "Dual ethernet adapter don't work in Ubuntu but work in XP"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Gelatin on 2007-03-12
I just installed Ubuntu on my machine for the first time. Everything worked well until I started looking at the network configuration. My motherboard is equipped with dual ethernet adapters, and they work properly when I boot windows xp on the machine. However with Ubuntu, the ethernet adapters are not getting DHCP and I can't seem to contact the router even if I manually set the IP address. The motherboards' chipset is nforce 650i SLI and there are no updates to be found on the nvidia website so I'm kinda lost.

Any bright Ideas? Let it be said that I'm a total linux newbie, but I'm fairly good with hardware.

---

### Post by astrolabio on 2007-03-12
post the content of your /etc/network/interfaces  file here.

and also run lspci and post the result as well.

---

### Post by Gelatin on 2007-03-12
**Interfaces:**

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.71
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 192.168.1.70
netmask 255.255.255.0
gateway 192.168.1.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0


**lspci:**

00:00.0 Host bridge: nVidia Corporation Unknown device 03a3 (rev a2)
00:00.1 RAM memory: nVidia Corporation Unknown device 03ac (rev a1)
00:00.2 RAM memory: nVidia Corporation Unknown device 03aa (rev a1)
00:00.3 RAM memory: nVidia Corporation Unknown device 03a9 (rev a1)
00:00.4 RAM memory: nVidia Corporation Unknown device 03ab (rev a1)
00:00.5 RAM memory: nVidia Corporation Unknown device 03a8 (rev a2)
00:00.6 RAM memory: nVidia Corporation Unknown device 03b5 (rev a1)
00:00.7 RAM memory: nVidia Corporation Unknown device 03b4 (rev a1)
00:01.0 RAM memory: nVidia Corporation Unknown device 03ad (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 03ae (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 03af (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 03b0 (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 03b1 (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 03b2 (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 03b3 (rev a1)
00:02.0 RAM memory: nVidia Corporation Unknown device 03b6 (rev a1)
00:02.1 RAM memory: nVidia Corporation Unknown device 03bc (rev a1)
00:02.2 RAM memory: nVidia Corporation Unknown device 03ba (rev a1)
00:03.0 PCI bridge: nVidia Corporation Unknown device 03b7 (rev a1)
00:06.0 PCI bridge: nVidia Corporation Unknown device 03b9 (rev a1)
00:07.0 PCI bridge: nVidia Corporation Unknown device 03bb (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation Unknown device 0370 (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:13.0 PCI bridge: nVidia Corporation Unknown device 0376 (rev a2)
00:14.0 PCI bridge: nVidia Corporation Unknown device 0374 (rev a2)
00:15.0 PCI bridge: nVidia Corporation Unknown device 0374 (rev a2)
00:16.0 PCI bridge: nVidia Corporation Unknown device 0378 (rev a2)
00:17.0 PCI bridge: nVidia Corporation Unknown device 0375 (rev a2)
00:18.0 PCI bridge: nVidia Corporation Unknown device 0377 (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0295 (rev a1)
04:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

---

### Post by lamalex on 2007-03-12
change your interfaces files back to dhcp and then what does it say?

(delete address, subnet, gateway, and change static to dhcp)

---

### Post by dannyboy79 on 2007-03-12
if he is going to manually edit his interfaces file, doesn't he need to add in auto for eth0? also, just comment out all the rest, make it like this:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

also, definitely make sure you comment out the eth0 way at the bottom!

#auto eth0

---

### Post by Gelatin on 2007-03-12
Thanks for the help guys, now things look like this:

auto lo
iface lo inet loopback

auto eth 0
iface eth0 inet dhcp
#address 192.168.1.71
#netmask 255.255.255.0
#gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp
#address 192.168.1.70
#netmask 255.255.255.0
#gateway 192.168.1.1

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


#auto eth0


Can't ping though, and seems like it's not getting DHCP. Funny because if I just shut Ubuntu down and started winXP up and it works straight away..

---

### Post by dannyboy79 on 2007-03-12
first of all, what is your setup? computers, routers, modems etc etc? are you turning this box into a router cause you don't need both interfaces otheriwse? also your 0 is a space away from eth, that won't work. why don't you try this, open up a terminal, and type in
sudo mv /etc/network/interfaces /etc/network/oldinterfaces
this will rename your current interfaces file so you can have a fresh one created. then I want you to completely reboot the machine, when you come into ubuntu, go straight away to the system, admin, networking gui, and enable the interface that is connected to your dhcp server only!  you shouldn't have them both connected to a dhcp server, don't enable the other 1 yet. tell me if it's working. also, take the dns servers that your router uses (these are most likely your isp's dns servers) and put them inside the dns servers box within that same gui. now close that gui and you should be ok, but when you reboot your dns servers you entered will be gone because of your dhcp lease will be redone, so you need to add them into your /etc/dhcp3/dhclient.conf file after you uncomment the prepend line. make it look like this:

prepend domain-name-servers 208.67.222.222, 208.67.220.220;

or whatever the dns servers are that were in your routers config. For multiple addresses, separate with a comma and don't forget the semicolon at the end. then do sudo /etc/init.d/networking restart

and you should be ok and on the internet, then figure out how to enable the second interrface if you're going to be using your box as a router for an internal network.

please see post number 29 for very helpful troubleshooting: [http://ubuntuforums.org/showthread.php?t=186848&page=3&highlight=MCP55+Ethernet](http://ubuntuforums.org/showthread.php?t=186848&page=3&highlight=MCP55+Ethernet)

---

### Post by Gelatin on 2007-03-13
Hey guys,

I found out that this is a known problem with the MCP55 chipset. There seems to be no support yet for this chipset in most linux distributions and I decided to add an old PCI adapter I had lying around. It works like a charm now (until I do some newbie error and wreck the whole thing, hehe). Thanks for all the help, really appreciate it!

---

### Post by dannyboy79 on 2007-03-13
> **Gelatin said:**
> Hey guys,

I found out that this is a known problem with the MCP55 chipset. There seems to be no support yet for this chipset in most linux distributions and I decided to add an old PCI adapter I had lying around. It works like a charm now (until I do some newbie error and wreck the whole thing, hehe). Thanks for all the help, really appreciate it!


despite you being new to linux you should still solve this issue as it will give you confidence that you can solve other issues. it's not a hard fix either. go to the link I provided and you can read the solution for yourself. many others are most likely in the same boat and if another person beside the link I posted also solved the issue you would pave the way for other newbies. it's obviously up to you but what if your next issue you don't have a piece of hardware lying around? are you going to go and through money at the problem instead of diving into linux and learning stuff? resolving this will only make more comfortable with linux and will teach you some of the behind the scenes stuff which is important for understanding why stuff happens. I hope you give it a try and I am sure others do as well since they may come to this thread and read all the threads but when they get to the end, they'll only see that used another card instead of resolving the issue with the current card. it has to do with the driver. good luck either way and welcome to linux

---

### Post by Gelatin on 2007-03-13
I should have mentioned that I went through both your suggestions and "post #29" and both tought me alot. However when that didn't fix things, I went googling for reviews for my motherboard and found one that mentioned the incompatibility of the network chipset. Then I googled some more and I wasn't able to find anyone that had found working drivers for it.

Since I'm familiar with maintainance and repair of windows operating systems I often turn to Linux for this "I don't have a clue what I'm doing but I'm going to find out" sensation.

---

### Post by dannyboy79 on 2007-03-13
well you must not have read back far enough in the thread because apparently the solution is very simple but depends on what version of the forcedeth you have installed and also what kernel. some suggest that a 15 second unplug of the power cord before you boot ubuntu will solve this because dual booting windows leave the ethernet in a state that doesn't allow the forcedeth driver to work properly. i know this doesn't sound like a solution but when going back and forth between windows it wouldn't be the worst to have to wait and extra 15 secs before powering up ubuntu. check it out here: [http://www.nvnews.net/vbulletin/showthread.php?t=71148&highlight=forcedeth](http://www.nvnews.net/vbulletin/showthread.php?t=71148&highlight=forcedeth)

---

### Post by Gelatin on 2007-03-14
I'll try this out tonight. Thanks.

---

