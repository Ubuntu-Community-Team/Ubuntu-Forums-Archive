---
title: "Hi from Newbee"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by mj295 on 2008-01-19
Hi All

A thread to say hello and tell you where I got to so far:

1. picked up a lap top from Tesco with a shiney new vista install.....
    Hardware wise : sony vaio NR10E

2. managed to re-partition the hard drive and stole 50Gb for an Ububtu partition

3. installed Ubuntu 7.10, luckily it automatically sorted out the dual boot menu thingy.

4. Vista still works fine - Im using it now
    Ubuntu boots and seems to work ok, but with no networking.

5. I'm currently loking around the forum to get the wireless working, problem is I have to reboot each time to swith between Vista with woking internet and Ubuntu to try out what i find :-(

6. trying to understand ndiswrapper amoungst other things

Anyhow - hello all, Im sure I will be asking for help soon.

Mark

---

### Post by meborc on 2008-01-19
hello,

it would be very helpful for us to know the make and model of your wireless card/chip

try typing```
lspci
```in the terminal and post here the output

---

### Post by bwhite82 on 2008-01-19
Welcome Mark! I do a lot of pointing to the Wiki (many new users do not know it exists) and it contains a lot of valuable information. [Here it is.]("http://help.ubuntu.com/community")

---

### Post by mj295 on 2008-01-19
Thanks both

I got this error when running the make for ndiswrapper

make[1]: Entering directory `/home/mark/Desktop/ndiswrapper-1.51/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
etc
etc
etc

So something is missing. Ill try to ind out what network card I have, but im in Vista at the minute, dont want to reboot again if I can help it.

---

### Post by mj295 on 2008-01-19
OK from windows, network card is

Atheros Communications Inc.
LAN-Express AS IEEE 802.11g PCI-E Adapter

I'll reboot and check what Ubuntu thinks it is

---

### Post by bwhite82 on 2008-01-19
Do you have the packages: build-essential automake autoconf gcc installed?

---

### Post by mlentink on 2008-01-19
First of all, Atheros chipset should be supported out of the box (they did for me)
Secondly, you shouldn't need to compile ndiswrapper from source, as it is available from ther repo's, and, afaik on the install-cd as well.


Edit: if you can find it on the cd, look it up in that other OS and look here: [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/)

---

### Post by candtalan on 2008-01-19
Are you sure you have to use ndiswrapper? What I mean is, are you sure that the driver for your onboard wireless chip is not already included in 7.10?

Also, I sort of recall that ndiswrapper may be readily available in ubuntu - if it is not already installed, then it may be in repositories just waiting for you to use synaptic etc etc.
hth

---

### Post by mj295 on 2008-01-19
> **Soldierboy said:**
> Do you have the packages: build-essential automake autoconf gcc installed?

Erm what does that mean?
where do I get those from?

I have not installed anything other than the 7.10 DVD which I downloaded  week or so ago.
Im also going to have a go at plugging directly in to my router to bypass the wireless, that will remove the need to keep rebooting. Luckily my USB storage key works on both OS's so I am using that to transfer files.

lspci -
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

---

### Post by bwhite82 on 2008-01-19
> **mj295 said:**
> Erm what does that mean?
where do I get those from?

I have not installed anything other than the 7.10 DVD which I downloaded  week or so ago.
Im also going to have a go at plugging directly in to my router to bypass the wireless, that will remove the need to keep rebooting. Luckily my USB storage key works on both OS's so I am using that to transfer files.

lspci -
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

Those are compiling tools if you want to compile apps from source, but as previously mentioned, no need to do this for ndiswrapper. I have to ask (as I have had this problem in the past): Is there a button on your computer chassis that turns on or off wireless? If so, have you pushed it?

---

### Post by mlentink on 2008-01-19
Again: you should ***not*** have to compile ndiswrapper form source, so do not bother with the build-essentials stuff. 
Atheros-chipset-based WiFicards are well supported in Ubuntu natively, so you shouldn't even have to use ndiswrapper.

Have you look at available networks in network-manager yet? You should see it's icon in the system-tray in the upper right of your screen. Obviously, you will need to give it your WEP or WPA passphrase (password)

---

### Post by mj295 on 2008-01-19
OK

Thanks all, I guess I am jumping in much deeper than I need to.

The wireless switch is on, would it help if I turn it off and back on again? As i said before I am rebooting back to Vista to get on the net and type in here. So i know the hardware is working.

Also

I have noticed this:
mark@mark-laptop:~$ sudo lshw -C network
[sudo] password for mark:
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
mark@mark-laptop:~$ 

I'm sure it should not be UNCLAIMED ???

When I open the network window I only get the wired network and the modem.

I did disable the restricted driver as per a post on here, was this the wrong thing to do?

---

### Post by bwhite82 on 2008-01-19
Um, I'm pretty sure you should ENABLE the restricted driver....
Then post the output of the command:

> sudo ifconfig -a

---

### Post by mlentink on 2008-01-19
> **Soldierboy said:**
> Um, I'm pretty sure you should ENABLE the restricted driver....


+1

Please ENable those restricted drivers. At the risk of sounding like a bore, the Atheros chipset is very well supported in Ubuntu, I have two pc's with Atheros installed and both were recognized immediately and worked out of the box.  How about network-manager?

---

### Post by mj295 on 2008-01-19
ok with just the restricted driver - there was no sign of the wireless network.

BUT

Ihave managed to use ndiswrapper and install the driver that way. The wireless option is now available. I have put the necessary password in and am typing this using the wireless connection. ????

Ah well. wonder if it will work after a reboot?

---

### Post by mlentink on 2008-01-19
Weird. 

But hey, if it works, it works....

---

### Post by mj295 on 2008-01-19
Thanks for the help and suggestions.

ok whats next...

I'd like to get skype working and some sort of messenger (I use MSN on windows)

looking at the skype web site I need
    *  Software requirements
    * Qt 4.2.1+
    * D-Bus 1.0.0
    * libsigc++ 2.0.2
    * libasound2 1.0.12

are these simple to install?
Also sykpe version is for 7.04 I have 7.10 will this matter?

Its a good job I'm off work next week, ill need plenty of time to get my head around this lot.

Mark

---

### Post by fatality_uk on 2008-01-19
> **mj295 said:**
> Thanks for the help and suggestions.

ok whats next...

I'd like to get skype working and some sort of messenger (I use MSN on windows)

looking at the skype web site I need
    *  Software requirements
    * Qt 4.2.1+
    * D-Bus 1.0.0
    * libsigc++ 2.0.2
    * libasound2 1.0.12

are these simple to install?
Also sykpe version is for 7.04 I have 7.10 will this matter?

Its a good job I'm off work next week, ill need plenty of time to get my head around this lot.

Mark

Use the Synaptic package manager to install aMsn. It's an MSN clone, funnily enough.
Skype is also available from there.

Hope this helps

---

### Post by mlentink on 2008-01-19
If I'd be allowed to offer advice...

If you need to install software in ubuntu you might want to try the followiing:
1. Go to Applications>Add/Remove Software and search for it there
2. Go to System>Administration>Synaptic Package Manager and search for it there
3. Google for a .deb installer on the 'net
4. Google for a binary installer file
5. If all the above fail then, and only then, try to find a source (usually compressed in a .tar.gz file

There are excellent howto's on installing stuff in ubuntu in the wiki (help.ubuntu.com) but also [here]("http://www.psychocats.net/ubuntu/") and [here]("http://monkeyblog.org/ubuntu/installing/") 

Compiling from sources can be daunting to the newbie, but usually is pretty straightforward if you follow the instructions.

Best of luck!

---

### Post by meborc on 2008-01-19
i suggest using pidgin (already installed, in the applications - internet menu) for msn... it has a much better (sleak) look then the amsn package available for ubuntu

one BIG suggestion, befor installing anything from source (tar balls etc) PLEASE READ THIS - [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) after reading this you will feel much comfotrable about installing stuff on your new ubuntu box

have fun, and lets hope you get everything set up as you like

also visit this page - [www.ubuntuguide.org](www.ubuntuguide.org) and this [https://wiki.ubuntu.com](https://wiki.ubuntu.com) to search for issues you need solving

;)

---

