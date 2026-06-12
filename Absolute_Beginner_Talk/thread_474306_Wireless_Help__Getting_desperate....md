---
title: "Wireless Help | Getting desperate..."
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-14
Hey.

First off, the community has been sooooo helpful. I love the ubuntu OS so far! But I have one question. Well, right now, I have a long ethernet  cable streaming down to my modem in the basement, through two windows. :P

I have **NO IDEA **how to install the driver(s) for any wireless card, and I'm going to need a step by step guide by someone. :( I've tried other things, but I can't get it to work. Can someone help me out?

My Wifi card (desktop):
```
Marvell Technology Group Ltd.
88w8335 [Libertas] 802.11b/g Wireless

```

No idea where to start. Thanks in advance. :)

---

### Post by Crafty Kisses on 2007-06-14
> **alecwh said:**
> Hey.

First off, the community has been sooooo helpful. I love the ubuntu OS so far! But I have one question. Well, right now, I have a long ethernet  cable streaming down to my modem in the basement, through two windows. :P

I have **NO IDEA **how to install the driver(s) for any wireless card, and I'm going to need a step by step guide by someone. :( I've tried other things, but I can't get it to work. Can someone help me out?

My Wifi card (desktop):
```
Marvell Technology Group Ltd.
88w8335 [Libertas] 802.11b/g Wireless

```

No idea where to start. Thanks in advance. :)
You probably have to use "NDISWrapper"

The second choice is go into terminal and type:
```
ndisgtk
```

---

### Post by alecwh on 2007-06-15
How do I use NDSWrapper? :(

---

### Post by kevdog on 2007-06-15
Can you tell me more about your card.  Is it for a laptop via a PCMCIA slot or is it for a desktop located in the pci slot??  Or could it be integrated into the MOBO??

---

### Post by alecwh on 2007-06-15
Sorry, it's in my DESKTOP, PCI Slot.

It has an antenna sticking out.

---

### Post by kevdog on 2007-06-15
No reason to be sorry, this doesnt mean it will not work.  Can you tell me the results of two commands (and I'll give you examples)

#1 - lspci
Looking for info about network controller
Example: 
06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

#2 - Using the number found in the above command -- In example case number is 06:00.0 -- give me the line corresponding when issuing the command:
lspci -n

Example:
06:00.0 0280: 14e4:4320 (rev 03)

Since you have an internet connection already. I think we can blow through this installation

---

### Post by alecwh on 2007-06-15
1.
```

02:02.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

```

2. 
```

02:05.0 0200: 11ab:4320 (rev 13)
02:02.0 0200: 11ab:1faa (rev 03)


```

Added both just incase.

---

### Post by alecwh on 2007-06-15
Don't want to start a new topic, so, bump. :(

---

### Post by kevdog on 2007-06-15
I only need info on wireless interface.

OK Im posting a link for the driver you need.  Its a zip file that I want you to extract in ~/temp/driver.
Note you may need to make this directory.  Im only suggesting this directory structure because I will be referring to it later on.

I also want you to install the following package:
sudo aptitude install build-essential

And I want you to download the ndiswrapper source tarball from: [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.47.tar.gz?modtime=1181699252&big_mirror=0](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.47.tar.gz?modtime=1181699252&big_mirror=0)
Place this into ~/temp/ndiswrapper

Extract this archive with the following command:
tar -zxvf ndiswrapper-*version*.tar.gz

Again substitute your appropriate version number where it says version.

Do you already have ndiswrapper installed??

---

### Post by kevdog on 2007-06-15
Calm down -- no bumping -- I need time to find the links for you!

---

### Post by alecwh on 2007-06-15
Sorry, glad you came back. :D

I don't have ndiswrapper. Don't know where you get it.

---

### Post by alecwh on 2007-06-15
Ok, I just DLed NDISwrapper.

EDIT: and did everything else, except you didn't post the driver

---

### Post by kevdog on 2007-06-15
What??? You need to be clear so I can help you.  Did you download all those files I asked??

---

### Post by kevdog on 2007-06-15
Sorry, I guess I didnt post the driver.  Here is the link:
[http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip](http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip)

I dont know what is in this zip file.  I specifically want the XP drivers.

---

### Post by alecwh on 2007-06-15
Ok.

I'm currently downloading the drivers.

I have downloaded, and extracted NDNSWrapper or whatever. I installed that other program you wanted me to.

Now it just finished, the files in the ZIP are:

Mrv8000c.cat
Mrv8000c.inf
Mrv8000c.sys

They ARE XP

---

### Post by kevdog on 2007-06-15
Ok lets first compile ndiswrapper

cd ~/temp/ndiswrapper/ndiswrapper-*version*

make distclean
make
sudo make install

Give me the output of:
ndiswrapper -v

---

### Post by alecwh on 2007-06-15
alec@AlecDesktop:~/temp/ndiswrapper-1.47$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586

---

### Post by kevdog on 2007-06-15
Congrats -- If you have never done it before, you have now compiled and installed a module strictly from source.  Something to be proud of.

Ok, now lets wrap the driver inside ndiswrapper.

cd ~/temp/driver  (or the directory where you have the driver files)

sudo ndiswrapper -i ******.inf   (Substitute the name of the .inf file here.  Make sure the .sys file is in the same directory)

Lets verify before moving forward that everything is OK.  Please post:
ndiswrapper -l

---

### Post by alecwh on 2007-06-15
```

alec@AlecDesktop:~/temp/driver$ ndiswrapper -l
mrv8000c : driver installed
        device (11AB:1FAA) present
alec@AlecDesktop:~/temp/driver$ 


```

---

### Post by kevdog on 2007-06-15
Ok two more big steps

Ndiswrapper essentially functions to wrap a windows driver to make it appear like a linux driver.  We know need o insert our new ndiswrapper/wireless driver into the linux kernel

sudo depmod -a  (make sure no errors occur with this command)
sudo modprobe ndiswrapper

Ok check if this inserted driver into kernel
dmesg

Look for line that will say something like:
ndiswrapper version version loaded

Great now lets make this run at boot time:
sudo ndiswrapper -m

By default ndiswrapper refers to your wireless interface as wlan0.  Probably ubuntu right now refers to your wireless card as either eth0 or eth1.

Can you post two things:
1. cat /etc/network/interfaces
2. ifconfig

Almost done -- I promise.

---

### Post by alecwh on 2007-06-15
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```


2.
```

eth0      Link encap:Ethernet  HWaddr 00:1A:4D:61:E0:29  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe61:e029/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:108721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74018 errors:0 dropped:0 overruns:0 carrier:0
          collisions:6 txqueuelen:1000 
          RX bytes:141164285 (134.6 MiB)  TX bytes:7855287 (7.4 MiB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:185176 (180.8 KiB)  TX bytes:185176 (180.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:18:E7:1B:37:F9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:e4000000-e4010000 

wlan0:ava Link encap:Ethernet  HWaddr 00:18:E7:1B:37:F9  
          inet addr:169.254.7.241  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:e4000000-e4010000 


```

---

### Post by kevdog on 2007-06-15
Ok, maybe everything is just about there -- 

First lets edit your interfaces file and take out some of the crap -- you dont have 5 wired/wireless cards.

sudo cp /etc/network/interfaces /etc/network/interfaces.bak
gksu gedit /etc/network/interfaces

Make your interfaces file look like this:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



Ok -- lets me just ask you a couple of things
If using gnome, you may want to install network-manager-gnome:
sudo aptitude install gnome-network-manager

This may be installed already, but Im not sure.  

Lastly if you are using a router, at least for now, turn off all encryption -- no WEP, no WPA for now.  Write down or just remember the ssid.  Make sure dhcp is enabled  (Im sure it is).

Ok reboot now!  Make sure to at unhook the wired connection

Report back

---

### Post by alecwh on 2007-06-15
uhmm, it says:


/etc/network is a directory.
Please check that you typed the location correctly and try again.

---

### Post by kevdog on 2007-06-15
sorry its /etc/network/interfaces

---

### Post by alecwh on 2007-06-15
Ok. Done with that. 

I did this, and got an error:
```

alec@AlecDesktop:~$ sudo aptitude install gnome-network-manager
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "gnome-network-manager"
The following packages have been kept back:
  gnome-btdownload hal hal-device-manager libhal-storage1 libhal1 
0 packages upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
alec@AlecDesktop:~$ 


```

---

### Post by kevdog on 2007-06-15
Its network-manager-gnome.

I have a hard time remembering these package names off the top of my head.

---

### Post by gcos7 on 2007-06-15
Perhaps it's just network-manager (that's what I downloaded and it works fine for me).;)

---

### Post by kevdog on 2007-06-15
Side note -- you need to update your system -- kind of like windows update

sudo aptitude update && sudo aptitude upgrade

---

### Post by alecwh on 2007-06-15
Ok, I have int installed alerady.

Where can I find it? (when I reboot)

---

### Post by kevdog on 2007-06-15
There should be an applet on the upper left part of the screen, that you can right click on.  

If that doesnt work, lets just test a few things:

Give output of:
ifconfig

iwlist wlan0 scanning

If with the last command, it lists your network, you know that the card can see your router.

This is the point that we might have a problem due to the driver issue.  Remember we guessed that this was the right XP driver. I hope it is.

---

### Post by alecwh on 2007-06-15
It Worked!

I am so happy right now. Thanks so much, I really really appreciate it. Holy crap, these forums are so cool. I finally have my system running at 100% of what it's meant to be.

<3 ubuntu

---

### Post by alecwh on 2007-06-15
KevDog, you are the man. If you ever need anything, PM me!

---

### Post by kevdog on 2007-06-15
Just a fine point -- your system will never be 100%.  Just when you think you have everything installed and running, you are going to want to tweak something.  Just a suggestion to get you on your way -- for example WPA wireless encryption -- if your router supports this.

Make sure to update and upgrade often:
sudo aptitude update && sudo aptitude upgrade

---

