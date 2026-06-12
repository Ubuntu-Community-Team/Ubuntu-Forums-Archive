---
title: "nooooo more troubles with network"
date: 2005-08-19
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-08-19
my microsoft broadband networking wireless usb adapter model MN-510 
i cannot find drivers for it so how am i supost to get it to work. it does connect through a usb.

---

### Post by adwait on 2005-08-19
Your MICROSOFT broadband networking adapter? Hmm............Good Luck finding Linux drivers for THAT!! :D

---

### Post by jasonpeinko on 2005-08-19
i have ndiswapper (dont know if i spelt that right) but i just need the windows drivers

---

### Post by jasonpeinko on 2005-08-25
[QUOTE=jasonpeinko]i have ndiswapper (dont know if i spelt that right) but i just need the windows drivers[/QUOTE]
 should i do this:
get another internal networking that i know will work with ndiswrapper?
and if so what one do you recomend that is cheap.

---

### Post by sneax on 2005-08-25
Wow I didn't know microsoft makes network products. Anyway, isn't this google search helpfull:
[http://www.google.be/search?hl=nl&q=MN-510+usb+network+linux&btnG=Zoeken&meta=](http://www.google.be/search?hl=nl&q=MN-510+usb+network+linux&btnG=Zoeken&meta=)
Or this:
[http://www.google.be/search?hl=nl&q=MN-510+usb+ubuntu&btnG=Zoeken&meta=](http://www.google.be/search?hl=nl&q=MN-510+usb+ubuntu&btnG=Zoeken&meta=)

?

---

### Post by Nequeo on 2005-08-25
[QUOTE=jasonpeinko]should i do this:
get another internal networking that i know will work with ndiswrapper?
and if so what one do you recomend that is cheap.[/QUOTE]
 Linux has trouble with newer wifi devices. It's not really 'Linux's fault', as such. Companies like Broadcom refuse to make Linux drivers, or provide the information needed to allow other Linux hackers to create them.

USB wireless devices are especially trouble-some. If you all you really use the wireless network for is internet access (i.e. you don't need to share 700mb movie files between computers), I would definately reccomend buying an old (even second hand) 11mb/s internal network card.

I have an old D-link 'Air' 11mb/s PCI network card. Must be something like 5 years old by now. When I installed Ubuntu a few months ago it automatically detected the card... detected that the strongest network signal was WEP encrypted, prompted me for the network key, then configured an IP address automatically. Smooth, simple, painless.

Most standard 'big brand' 54mb/s internal wireless cards will work with NDIS wrapper. Linksys, D-link, and so forth... But you might have a bit of a battle getting them working.

---

### Post by jasonpeinko on 2005-09-05
[QUOTE=Nequeo]Linux has trouble with newer wifi devices. It's not really 'Linux's fault', as such. Companies like Broadcom refuse to make Linux drivers, or provide the information needed to allow other Linux hackers to create them.

USB wireless devices are especially trouble-some. If you all you really use the wireless network for is internet access (i.e. you don't need to share 700mb movie files between computers), I would definately reccomend buying an old (even second hand) 11mb/s internal network card.

I have an old D-link 'Air' 11mb/s PCI network card. Must be something like 5 years old by now. When I installed Ubuntu a few months ago it automatically detected the card... detected that the strongest network signal was WEP encrypted, prompted me for the network key, then configured an IP address automatically. Smooth, simple, painless.

Most standard 'big brand' 54mb/s internal wireless cards will work with NDIS wrapper. Linksys, D-link, and so forth... But you might have a bit of a battle getting them working.[/QUOTE]
 ok thx. what companies have linux drivers?

---

### Post by Steve1961 on 2005-09-05
I've recently installed a belkin F5D7000UK ver 3 PCI card.  It has a ralink chipset and and linux drivers are available for it.  It's very easy to set up and works great.  See this wiki entry for details:

[https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo)

---

### Post by jasonpeinko on 2005-09-05
where did u buy it?

---

### Post by Steve1961 on 2005-09-05
I bought it at a local pc world store in the UK.  But if you don't live in the UK, and it's not available locally, you could always order it from one of the online retailers, e.g.

[http://www.ebuyer.com/customer/products/index.html?action=c2hvd19wcm9kdWN0X292ZXJ2aWV3&product_uid=45622](http://www.ebuyer.com/customer/products/index.html?action=c2hvd19wcm9kdWN0X292ZXJ2aWV3&product_uid=45622)

---

### Post by jasonpeinko on 2005-09-05
does linksys make linux drivers? because i want to get the card today because i have to start school tomarrow.

---

### Post by az on 2005-09-05
[QUOTE=jasonpeinko]i have ndiswapper (dont know if i spelt that right) but i just need the windows drivers[/QUOTE]


Did you try ndiswrapper?  You need to install the ndiswrapper-utils package and then run this from a terminal:

sudo ndiswrapper -i (driver.inf)  #where (driver.inf) is your windows driver for the device.  You should get it off the driver cd you got with the device.  Put it on the desktop and cd there
cd /Desktop

sudo ndiswrapper -i (driver.inf)
sudo ndiswrapper -l
sudo modprobe ndiswrapper 

then go to the networking configurator and configure your connection.  If everything works, add the word "ndiswrapper" at the end of /etc/modules

sudo gedit /etc/modules

---

### Post by jasonpeinko on 2005-09-05
[QUOTE=azz]Did you try ndiswrapper?  You need to install the ndiswrapper-utils package and then run this from a terminal:

sudo ndiswrapper -i (driver.inf)  #where (driver.inf) is your windows driver for the device.  You should get it off the driver cd you got with the device.  Put it on the desktop and cd there
cd /Desktop

sudo ndiswrapper -i (driver.inf)
sudo ndiswrapper -l
sudo modprobe ndiswrapper 

then go to the networking configurator and configure your connection.  If everything works, add the word "ndiswrapper" at the end of /etc/modules

sudo gedit /etc/modules[/QUOTE]
 ok i cant find the disk so i go to download it and it is an exe
what do i do?

---

### Post by jasonpeinko on 2005-09-05
[QUOTE=jasonpeinko]ok i cant find the disk so i go to download it and it is an exe
what do i do?[/QUOTE]
 nvm 
this is what i get:
```

Installing wusb54gv2
jason@ubuntu:~/Desktop$ ndiswrapper -l
Installed ndis drivers:
foobar  invalid driver!
wusb54gv2       driver present
jason@ubuntu:~/Desktop$ sudo modprobe mdiswrapper
FATAL: Module mdiswrapper not found.
jason@ubuntu:~/Desktop$

```

---

### Post by Steve1961 on 2005-09-06
Let me just make sure I know what the problem here is.  You downloaded an .exe file containing the windows drivers and then tried to install this file with ndiswrapper?  If so, this is the problem.  You first need to extract the .inf and .sys files from the .exe file.  I'm not sure how you do this in linux but you can certainly do it in windows with packages such as winzip.  Once you have the files you need to start again, but first clear out the clutter from the first attempt.  Type ndiswrapper -e wusb54gv2 to unload the driver.  Then type the following:

sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

This will get rid of the ndiswrapper version included with Ubuntu.  I've had much more success with version 1.2.  Just follow the steps in this thread that I followed to install a broadcom driver.

[http://ubuntuforums.org/showthread.php?p=334239#post334239](http://ubuntuforums.org/showthread.php?p=334239#post334239)

---

### Post by brinebold on 2005-09-06
With a wireless NIC check to find the chipset it uses using the *lspci* command in your terminal.  Find your wireless card there and check the chipset manufacturer's website for drivers.
I had the same problem you are having with my Linksys WMP54G v4 card.  Linksys did not have any Linux support period but Railink, the company that sold them the chipset, did.  I installed them and it worked fine after that.  All the end manufacturers do is selcect a chipset, stick it on their card, slap an antenna on the back and give you a few utilities.  The chipset drivers are generally all you need.

---

### Post by jasonpeinko on 2005-09-08
how do i tell what version i have i dont know if i have 1 2 or 4?

---

### Post by jasonpeinko on 2005-09-11
[QUOTE=jasonpeinko]how do i tell what version i have i dont know if i have 1 2 or 4?[/QUOTE]
 well after all that work i found the disk that came with it and i installed the drivers and everything went fine but nothing is diffrent the the networking area it is the exact same should there be another catagory? or is it still ethernet? what should it look like? 
Thank you very much for your patients and help.

---

### Post by Steve1961 on 2005-09-12
Sorry to tell you this, but there should be another entry in the networking windows called something like wlan0.  When you type sudo ndiswrapper -l in the terminal what does it say.  It looks like the driver isn't working.

---

### Post by jasonpeinko on 2005-09-12
[QUOTE=Steve1961]Sorry to tell you this, but there should be another entry in the networking windows called something like wlan0.  When you type sudo ndiswrapper -l in the terminal what does it say.  It looks like the driver isn't working.[/QUOTE]
 nothin
in the pull down  bar there is wlan0

---

### Post by jasonpeinko on 2005-09-12
ok scratch everything else.
here is where im at i installed the drivers here is everything i typed
```

jason@ubuntu:~$ cd Desktop
jason@ubuntu:~/Desktop$ mkdir wirelessdrivers
jason@ubuntu:~/Desktop$ cd wirelessdrivers
jason@ubuntu:~/Desktop/wirelessdrivers$ sudo ndiswrapper -i Rt2500.INF
Password:
ls: /etc/ndiswrapper: No such file or directory
Installing rt2500
jason@ubuntu:~/Desktop/wirelessdrivers$ ndiswrapper -i Rt2500.INF
rt2500 is already installed. Use -e to remove it
jason@ubuntu:~/Desktop/wirelessdrivers$ sudo ndiswrapper -l
Installed ndis drivers:
rt2500  driver present
jason@ubuntu:~/Desktop/wirelessdrivers$ sudo modprobe ndiswrapper
jason@ubuntu:~/Desktop/wirelessdrivers$

```
then everything stays the same under network settings.
dont know how to get a pic up if you need to see it.

---

### Post by Steve1961 on 2005-09-13
I see the problem.  The rt2500 driver is for the ralink chipset.  This has native linux drivers available so your problems should soon be sorted.  Forget all about ndiswrapper.  I couldn't get a ralink chipset to work with it either.  Just follow the how to in the link below and you should be good to go.

[https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo)

Once you've downloaded and installed the wireless drivers you should have another entry in your networking menu called ra0.  You don't need to bother with the raconfig part of the how to.  You can configure the essid and any encryption from the gui.

---

### Post by jasonpeinko on 2005-09-13
[QUOTE=Steve1961]I see the problem.  The rt2500 driver is for the ralink chipset.  This has native linux drivers available so your problems should soon be sorted.  Forget all about ndiswrapper.  I couldn't get a ralink chipset to work with it either.  Just follow the how to in the link below and you should be good to go.

[https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo)

Once you've downloaded and installed the wireless drivers you should have another entry in your networking menu called ra0.  You don't need to bother with the raconfig part of the how to.  You can configure the essid and any encryption from the gui.[/QUOTE]
 here is what i now get
```

jason@ubuntu:~/Desktop/rt2500-1.1.0/Module$ sudo insmod rt2500.ko
insmod: error inserting 'rt2500.ko': -1 File exists
jason@ubuntu:~/Desktop/rt2500-1.1.0/Module$


```

---

### Post by jasonpeinko on 2005-09-14
[QUOTE=jasonpeinko]here is what i now get
```

jason@ubuntu:~/Desktop/rt2500-1.1.0/Module$ sudo insmod rt2500.ko
insmod: error inserting 'rt2500.ko': -1 File exists
jason@ubuntu:~/Desktop/rt2500-1.1.0/Module$


```[/QUOTE]
 any ideas? should i erase everything an start again? how do i erase it?

---

### Post by Steve1961 on 2005-09-14
To be honest I'm not sure what the problem is.  If I was you I'd clean everything out, including ndiswrapper, and start again.  When I tried the ralink driver it loader without an issue.

---

### Post by jasonpeinko on 2005-09-14
how do i unistall everything including the drivers

---

### Post by jasonpeinko on 2005-09-14
[QUOTE=jasonpeinko]how do i unistall everything including the drivers[/QUOTE]
 plz help i really need this working for school

---

### Post by jasonpeinko on 2005-09-15
[QUOTE=jasonpeinko]plz help i really need this working for school[/QUOTE]
 can i just go in and delet the file by hand?

---

### Post by Steve1961 on 2005-09-16
First make sure you've got rid of all remnants of ndiswrapper.  You'll find the instructions here:

[http://www.ubuntuforums.org/showthread.php?t=63633](http://www.ubuntuforums.org/showthread.php?t=63633)

You then need to clean up the linux driver.  One way that might work is to CD to where you put the source code and type sudo make uninstall.  If this doesn't work I've found a thread on another forum that you could try:

[http://forums.fedoraforum.org/showthread.php?t=60081](http://forums.fedoraforum.org/showthread.php?t=60081)

After that try again.  Best of luck

---

### Post by jasonpeinko on 2005-09-16
[QUOTE=Steve1961]First make sure you've got rid of all remnants of ndiswrapper.  You'll find the instructions here:

[http://www.ubuntuforums.org/showthread.php?t=63633](http://www.ubuntuforums.org/showthread.php?t=63633)

You then need to clean up the linux driver.  One way that might work is to CD to where you put the source code and type sudo make uninstall.  If this doesn't work I've found a thread on another forum that you could try:

[http://forums.fedoraforum.org/showthread.php?t=60081](http://forums.fedoraforum.org/showthread.php?t=60081)

After that try again.  Best of luck[/QUOTE]
 ok i got it to this with no errors but there is nothing under networking
```

  CC      /home/jason/rt2500-1.1.0-b3/Module/rt2500.mod.o
  LD [M]  /home/jason/rt2500-1.1.0-b3/Module/rt2500.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
jason@ubuntu:~/rt2500-1.1.0-b3/Module$ sudo insmod rt2500.ko
Password:
jason@ubuntu:~/rt2500-1.1.0-b3/Module$


```

---

### Post by Steve1961 on 2005-09-18
To be honest I'm out of suggestions.  Sorry.  Can anyone help?

---

### Post by jasonpeinko on 2005-09-18
[QUOTE=Steve1961]To be honest I'm out of suggestions.  Sorry.  Can anyone help?[/QUOTE]
 yes can someone plz help

---

### Post by jasonpeinko on 2005-09-18
would it not be showing up because im using the wlan rignt now through a cable?

---

### Post by Steve1961 on 2005-09-19
Not sure what you mean by 'using the wlan through a cable'.  There should be two entries in the networking box - one for your wired ethernet, eth0, and another for yoru ralink wireless card, ra0.  In theory you should be able to see both.  You should deactivate eth0 and activate ra0.  It should be simply a case of clicking on ra0, going into properties to set your essid, and then pressing activate.

---

### Post by jasonpeinko on 2005-09-19
[QUOTE=Steve1961]Not sure what you mean by 'using the wlan through a cable'.  There should be two entries in the networking box - one for your wired ethernet, eth0, and another for yoru ralink wireless card, ra0.  In theory you should be able to see both.  You should deactivate eth0 and activate ra0.  It should be simply a case of clicking on ra0, going into properties to set your essid, and then pressing activate.[/QUOTE]
 there is no ra0
just eth0 i have a screen shot if u want
could it be there and not show up? could i like try and activate it through the teminal?

---

### Post by Steve1961 on 2005-09-19
You could try.  Type:

sudo iwlist ra0
sudo iwconfig ra0 essid (your essid name) 
iwconfig ra0 enc (your WEP key if you have one) 
sudo dhclient ra0 (to get an IP adress) 

However, it looks to me as if the driver isn't working so I'm not that hopeful.  You could also try disabling your wired network card in the bios to see if that makes a difference.

Are you absolutely sure you have a ralink card?

---

### Post by jasonpeinko on 2005-09-19
it is a rt2500 though.
I have the cd with drivers should i go back to trying to get it to work with ndiswrapper?

---

### Post by Steve1961 on 2005-09-20
Double check in the hardware browser to see if the system recognises the card (applications/system tools/hardware browser).  If it's not there try typing /sbin/lspci -v to see what your system has to say about the device - there should be some sort of entry.    For example, my wired eth0 card is shown as:

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7125
        Flags: bus master, 66Mhz, fast devsel, latency 0, IRQ 11
        Memory at febf9000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at f000 [size=8]
        Capabilities: <available only to root>

---

### Post by jasonpeinko on 2005-09-20
[QUOTE=Steve1961]Double check in the hardware browser to see if the system recognises the card (applications/system tools/hardware browser).  If it's not there try typing /sbin/lspci -v to see what your system has to say about the device - there should be some sort of entry.    For example, my wired eth0 card is shown as:

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 7125
        Flags: bus master, 66Mhz, fast devsel, latency 0, IRQ 11
        Memory at febf9000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at f000 [size=8]
        Capabilities: <available only to root>[/QUOTE]
 2 things code does not work and hardware browser is not there

---

### Post by Steve1961 on 2005-09-21
Apologies, I was using my fedora installation when I gave the instructions and forgot that it's slightely different in Ubuntu.  Just type sudo lspci -v.

---

### Post by MuRRe on 2005-09-21
i cannot even get ndiswrapper to work. it says:
sudo: ndiswrapper: command not found

[email]murre@aspire5024:~/Program/ndiswrapper-1.3rc1.tar.gz[/email]_FILES/ndiswrapper-1.3rc1$ make
make -C driver
make[1]: Entering directory `/home/murre/Program/ndiswrapper-1.3rc1.tar.gz_FILES/ndiswrapper-1.3rc1/driver'
Can't find kernel sources in /lib/modules/2.6.10-5-amd64-generic/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Fel 1
make[1]: Leaving directory `/home/murre/Program/ndiswrapper-1.3rc1.tar.gz_FILES/ndiswrapper-1.3rc1/driver'
make: *** [all] Fel 2
[email]murre@aspire5024:~/Program/ndiswrapper-1.3rc1.tar.gz[/email]_FILES/ndiswrapper-1.3rc1$ make install
make -C driver install
make[1]: Entering directory `/home/murre/Program/ndiswrapper-1.3rc1.tar.gz_FILES/ndiswrapper-1.3rc1/driver'
Can't find kernel sources in /lib/modules/2.6.10-5-amd64-generic/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Fel 1
make[1]: Leaving directory `/home/murre/Program/ndiswrapper-1.3rc1.tar.gz_FILES/ndiswrapper-1.3rc1/driver'
make: *** [install] Fel 2


murre@aspire5024:~$ sudo find /lib/modules/$murre -r -name "ndiswrapper*" -print
find: invalid predicate `-r'

---

### Post by jasonpeinko on 2005-09-21
[QUOTE=Steve1961]Apologies, I was using my fedora installation when I gave the instructions and forgot that it's slightely different in Ubuntu.  Just type sudo lspci -v.[/QUOTE]
```

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]        Subsystem: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
        Flags: bus master, 66MHz, medium devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [a0] AGP version 2.0
        Capabilities: [c0] Power Management version 2

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: e4000000-e5ffffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: [80] Power Management version 2

0000:00:09.0 FireWire (IEEE 1394): Lucent Microelectronics FW323 (rev 61) (prog-if 10 [OHCI])
        Subsystem: Lucent Microelectronics FW323
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at e6000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at d000 [size=256]
        Memory at e6001000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

0000:00:10.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: Soyo Computer, Inc: Unknown device a707
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at d400 [size=256]
        Capabilities: [c0] Power Management version 2

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
        Subsystem: VIA Technologies, Inc. VT8233A ISA Bridge
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: [c0] Power Management version 2

0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at d800 [size=16]
        Capabilities: [c0] Power Management version 2

0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at dc00 [size=32]
        Capabilities: [80] Power Management version 2

0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at e000 [size=32]
        Capabilities: [80] Power Management version 2

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01) (prog-if 00 [VGA])
        Subsystem: C.P. Technology Co. Ltd RV250 If [Radeon 9000 Pro "Evil Commando"]
        Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at c000 [size=256]
        Memory at e5000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [58] AGP version 2.0
        Capabilities: [50] Power Management version 2

0000:01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)
        Subsystem: C.P. Technology Co. Ltd: Unknown device 2038
        Flags: stepping, 66MHz, medium devsel
        Memory at d8000000 (32-bit, prefetchable) [disabled] [size=128M]
        Memory at e5010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [58] AGP version 2.0
        Capabilities: [50] Power Management version 2

jason@ubuntu:~$


```

---

### Post by Steve1961 on 2005-09-22
> **MuRRe]i cannot even get ndiswrapper to work. it says:
sudo: ndiswrapper: command not found

[email]murre@aspire5024:~/Program/ndiswrapper-1.3rc1.tar.gz[/email]_FILES/ndiswrapper-1.3rc1$ make
make -C driver
make[1]: Entering directory `/home/murre/Program/ndiswrapper-1.3rc1.tar.gz_FILES/ndiswrapper-1.3rc1/driver'
Can't find kernel sources in /lib/modules/2.6.10-5-amd64-generic/build said:**
> : *** [prereq_check] Fel 1
make[1]: Leaving directory `/home/murre/Program/ndiswrapper-1.3rc1.tar.gz_FILES/ndiswrapper-1.3rc1/driver'
make: *** [all] Fel 2
[email]murre@aspire5024:~/Program/ndiswrapper-1.3rc1.tar.gz[/email]_FILES/ndiswrapper-1.3rc1$ make install
make -C driver install
make[1]: Entering directory `/home/murre/Program/ndiswrapper-1.3rc1.tar.gz_FILES/ndiswrapper-1.3rc1/driver'
Can't find kernel sources in /lib/modules/2.6.10-5-amd64-generic/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Fel 1
make[1]: Leaving directory `/home/murre/Program/ndiswrapper-1.3rc1.tar.gz_FILES/ndiswrapper-1.3rc1/driver'
make: *** [install] Fel 2


murre@aspire5024:~$ sudo find /lib/modules/$murre -r -name "ndiswrapper*" -print
find: invalid predicate `-r'


I presume you've attempted to reinstall ndiswrapper.  The problem here is that you're missing the ndiswrapper kernel module. I know that you can install this in synaptic in the i386 version but I seem to remember it's missing in the AMD64 version.  This probably explains the problems that you've had previously with ndiswrapper.  Looking through the forums there doesn't appear to be any answer apart from installing 32 bit ubuntu.  In fact, even the ralink drivers won't work in 64 bit but should be fine in 32 bit.
From the output of lspci your card isn't recognised at all.

---

### Post by jasonpeinko on 2005-09-22
[QUOTE=Steve1961]I presume you've attempted to reinstall ndiswrapper.  The problem here is that you're missing the ndiswrapper kernel module. I know that you can install this in synaptic in the i386 version but I seem to remember it's missing in the AMD64 version.  This probably explains the problems that you've had previously with ndiswrapper.  Looking through the forums there doesn't appear to be any answer apart from installing 32 bit ubuntu.  In fact, even the ralink drivers won't work in 64 bit but should be fine in 32 bit.
From the output of lspci your card isn't recognised at all.[/QUOTE]
 so how do i get it to be reconized 
on boot up of the comp its green light flashes so it is in the slot

---

### Post by Steve1961 on 2005-09-25
Unless anyone else has any ideas?  I don't think you will get the card recognised.  Some hardware will just not work with some distros.  Try the 32 bit version of Ubuntu.

---

### Post by jasonpeinko on 2005-09-25
[QUOTE=Steve1961]Unless anyone else has any ideas?  I don't think you will get the card recognised.  Some hardware will just not work with some distros.  Try the 32 bit version of Ubuntu.[/QUOTE]
 willl the 32 bit work with my 64 amd? if not what is  the easyest crad to get to work?

---

### Post by Steve1961 on 2005-09-25
The 32 bit version will work just as well as the 64 bit version with your AMD64 - I've tried both and didn't notice any performance differences. However, you should have far less problems with the 32 bit, and should try to reinstall the ralink drivers once you get this up and running.  Failing that, just search this forum for an alternative wifi card.

---

