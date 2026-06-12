---
title: "Can't Find Internet Connection in Gutsy"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by geekchicohio on 2007-12-27
Hey all,
The humbling experience of Ubuntu continues.
To get out of an unusually buggy install and to deal with some hardware issues, I just today finished a fresh install of Gutsy.
For the first time on a fresh install my internet connection doesn't "just work."
I have 2 ethernet jacks in my computer, one in the mobo and one in a pci card (long story) and plugging the cable into either is fruitless.
In my network settings I've enabled wired connections and set them to dhcp but I don't really know how to ensure that linux even knows my ethernet jacks are there.
Any help in understanding this would be greatly appreciated, as I've been reduced to trying to solve this problem by coming here on my t-mobile sidekick.
Thanks so much.

---

### Post by jas0 on 2007-12-27
First make sure that you have your ethernet interfaces enabled by running the following commands:

```
sudo eth0 up && eth1 up
```

Also, ensure that you have a functioning device which can give out IP addresses (usually a router of some sort).

Plug a network cable into either port and make sure that there are lights on the network interface. If you do not see any lights, try a second network cable.

As soon as you have the lights, run the following commands:

```
sudo dhclient eth0 && dhclient eth1
```

If you do not get an ip address, plug the cable into the other interface and repeat the command.

If none of this works, just run a ifconfig and paste the output here for further analysis.

---

### Post by OffAxis on 2007-12-27
```
ifconfig
```
will list your network connections (hopefully). If you've been messing with your **/etc/network/interfaces** file you may not be correctly loading dhcp for the detected devices. 
can you post that file?

```
sudo /etc/init.d/networking restart
```
will requery the list.

---

### Post by spiderbatdad on 2007-12-27
[QUOTE=jas0;4023612]First make sure that you have your ethernet interfaces enabled by running the following commands:

```
sudo eth0 up && eth1 up
```

```
sudo dhclient eth0 && dhclient eth1
```


i think this needs to be sudo eth0 up && sudo eth1 up    then sudo dhclient eth0 && sudo dhclient eth1

---

### Post by jas0 on 2007-12-27
> **spiderbatdad said:**
> [QUOTE=jas0;4023612]First make sure that you have your ethernet interfaces enabled by running the following commands:

```
sudo eth0 up && eth1 up
```

```
sudo dhclient eth0 && dhclient eth1
```


i think this needs to be sudo eth0 up && sudo eth1 up    then sudo dhclient eth0 && sudo dhclient eth1

Good point. Nice catch.

---

### Post by geekchicohio on 2007-12-27
Hey all, 
First of all, ```
 sudo eth0 up && sudo eth1 up
``` provided me with ```
 sudo: eth0: command not found
```
the second command gave me a lot of feedback bedore telling me it could not create dhclient.leases, nor dhclient.pid due to denied permission and could not set group id because the operation was not allowrd. I believe the currently working port is eth0, because I'm told the network is down when commands are executed on behalf of eth1 (sorry for all the paraphrasing, I'm typing this into my web-enabled smartphone until I get this fixed.

Also, ifconfig gave me info on eth0, eth0:avah, and lo.
Until I know what I'm looking for it's hard to know what to transcribe here, sorry for the helplessness.

---

### Post by jas0 on 2007-12-28
> **geekchicohio said:**
> Hey all, 
First of all, ```
 sudo eth0 up && sudo eth1 up
``` provided me with ```
 sudo: eth0: command not found
```
the second command gave me a lot of feedback bedore telling me it could not create dhclient.leases, nor dhclient.pid due to denied permission and could not set group id because the operation was not allowrd. I believe the currently working port is eth0, because I'm told the network is down when commands are executed on behalf of eth1 (sorry for all the paraphrasing, I'm typing this into my web-enabled smartphone until I get this fixed.

Also, ifconfig gave me info on eth0, eth0:avah, and lo.
Until I know what I'm looking for it's hard to know what to transcribe here, sorry for the helplessness.

Let me give this another try without the brain fart.

```
sudo ifconfig eth0 up && sudo ifconfig eth1 up
sudo dhclient eth0 && sudo ifconfig eth1 up
```

Do these steps by first plugging the cable into the first interface and then into the second interface and trying to browse the internet. One of these interfaces do work, you just need to know which one. My guess is that it's probably the PCI network card.

---

### Post by geekchicohio on 2007-12-28
Thanks for you continued help. Unfortunately this didn't produce anything new. Every time I ran the first command you gave me I received ```
SIOCSIFFLAGS: No such file or directory
```
With the other command I received info that the network is down or that no dhcpoffers were received and no working leases in persistent database - sleeping.
Still nothing but can't find server errors when I open a browser.
Thanks for your help, but I'm still lost, here.

---

### Post by spiderbatdad on 2007-12-28
does this command produce a list of network devices: ```
sudo lshw -C Network
```


and I'm wondering, as a result of the error message if you have the packages in synaptic installed, shown in the picture below.

---

### Post by geekchicohio on 2007-12-28
Alright, that command produced info for my ethernet interface, ```
physical id: a
Bus info pci@0000:00:0a.0
Logical name: eth0
Version: 11
``` as well as it's serial, width, clock, capabilities, and configuration.
Also info on my wi-fi card (disabled) which is irrelevent, it's never been used this install and there's no wifi signal present here. The wifi card is eth1.

---

### Post by geekchicohio on 2007-12-28
I forgot to mention in my last post...
That picture is too small for me to see on my phone. I can tell you I have NO custom packages whatsoever, though. This is a fresh install of gutsy that has never had working internet in is 48ish hours of existence.
All I have is what comes on the livecd.

---

### Post by spiderbatdad on 2007-12-28
but no manufacturer or vendor...and all those zeros in the bus info don't look good either. I think this card lacks a driver? Or is broken...I'm not sure.  after the 3 or 4 zeros in the bus info, there should be a 2 or even 4 this means a driver installed. but if your card doesn't even list a vendor...I think its busterated.

---

### Post by spiderbatdad on 2007-12-28
the fresh install should have included network packages. were both your network devices plugged in when you tried the command? maybe try to discover the device by plugging them in one at a time. you should get a product and vendor name and bus info that looks something like:   bus info: pci@0000:02:08.0
 notice the 02:08.0    although the usb device may be better discovered by simply```
lspci
```

---

### Post by OffAxis on 2007-12-28
Let's take a step back for a moment;
Is your cable plugged ALL the way in?
How about the back of the router? Is it in the 'Uplink' spot?
Have you disabled the NIC in the bios?
Is it a known good cable?

This being the first time (on this machine) that it 'just didn't work' probably means a hardware issue.

Can you get to the network off the LiveCD?

---

### Post by spiderbatdad on 2007-12-28
edited because i was rude....i apologize.

---

### Post by geekchicohio on 2007-12-28
Sorry, keep in mind I'm transcribing via cell phone, here. There was a product description and vendor listed, I just didn't list them because I didn't think they were important to understanding how to make the thing work. It's an NC100 Network Everywhere Fast Ethernet 10/100
Vendor: ADMtek

---

### Post by OffAxis on 2007-12-28
So can you get an ip from the dhcp server with the LiveCD?

---

### Post by geekchicohio on 2007-12-28
Alright.
First of all, I'd like to take this opportunity to say I'm new(ish) to linux but not a total moron. I've tried multiple cables, and everything's plugged in the way it's supposed to be. Lspci gave me [/code]00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11) [/code]

---

### Post by spiderbatdad on 2007-12-28
there appears to be a linux driver available...[http://members.driverguide.com/driver/detail.php?driverid=334721](http://members.driverguide.com/driver/detail.php?driverid=334721) I'll see if I can find a tarball for you and upload it. Edited because you're on a phone :) and may return here for the link.

---

### Post by spiderbatdad on 2007-12-28
actually here's a tarball if you can download it.....below


read the install file included in the main directory;)  you'll want to run it as sudo make install

---

### Post by walkerk on 2007-12-28
You'll need your respective driver... 

And, the command to bring/down up a network interface is (where <interface> = your iface, ie: eth0, eth1, etc...)
```
sudo ifup <interface>
```
```
sudo ifdown <interface>
```

pull dhcp
```
sudo dhclient <interface>
```

restart networking
```
sudo /etc/init.d/networking restart/stop/start
```

---

### Post by spiderbatdad on 2007-12-28
posting again in case you cant see the other page on your mobile phone...heres a tarball of the driver...extract it. cd into the directory like```
cd Desktop
``` if you extract it on your desktop.Then ```
cd amd8211
```

 Then```
sudo make install
``` you should not need to make or configure...if you do there are other issues...see the install file in the main directory...

---

### Post by OffAxis on 2007-12-28
```
You'll need your respective driver
```
I don't get it...if the card is recognized, all the settings are there (vendor,width, clock, etc)...why reinstall a working driver?

---

### Post by spiderbatdad on 2007-12-28
because there are no numbers in the pci bus info.The card identifies itself, but a driver is not installed.

---

### Post by geekchicohio on 2007-12-28
I'm off to work now, hopefully tonight I'll be able to get online with someone else's computer and put that on a flashdrive. I'll let you all know what happens.

---

### Post by OffAxis on 2007-12-28
> because there are no numbers in the pci bus info.
true, but there is an 'a'. Isn't the listing for the pci essentially a path (and not a driver build version)? And since the card is being identified correctly, can't we assume that the path must be correct?
[http://ezix.org/project/wiki/HardwareLiSter#Businformationanddevicenumbering]("http://ezix.org/project/wiki/HardwareLiSter#Businformationanddevicenumbering")

The telltale thing that the OP didn't list from **lshw **was the 'configuration' line, which would list a driver if it was loaded.

On my system here I've got devices mapped to 'a', 'b', 'c', and 'e' and everything works fine.
```
sudo lspci -tv
```
will give a nice overview, and should have the 'NC100 Network Everywhere Fast Ethernet 10/100' attached to the '0a' node.

The OP also mentioned that he had 2 network cards installed, one on the mobo, so lshw should have returned both. The other might not be under 'network', but 'bridge' or 'ethernet', etc. The full lshw list (or possibly **lshw -short**)  is really the only way to tell.

---

### Post by spiderbatdad on 2007-12-29
what you posted looks good, however, on a pci to pci bridge I believe a **logical number** is first used by the pci or pcmcia device drivers to map to devices on a specified pci bus. of course for controllers and other types of mobo devices hex values are obviously used.

---

### Post by geekchicohio on 2007-12-29
Thanks a lot all, I've got the tarbell on my flashdrive now. I'll be headed home to hopefully get this sucker up and running.

---

### Post by geekchicohio on 2007-12-29
Hey all,
So I've attempted to install the driver you guys provided me and received a slew of errors and nothing to lead me to believe anything loaded properly. I'll do my best to painstakingly reproduce everything here... ```

/home/heff/adm8211/adm8211-hw.c:32:26: error: linux/config.h: No such file or directory
/home/heff/adm8211/adm8211-hw.c: in function 'adm8211-rx-skb':
/home/heff/adm8211/adm8211-hw.c:564: error: 'struct sk-buff' has no member named 'mac'
/home/heff/adm8211/adm8211-hw.c: in function 'adm8211-interrupt-rci':
/home/heff/adm8211/adm8211-hw.c:802: error: 'struct sk-buff' has no member named 'mac'
/home/heff/adm8211/adm8211-hw.c: in function 'adm8211-open':
/home/heff/adm8211/adm8211-hw.c:2030: Warning: 'deprecated-irq-flag' is deprecated (declared at include/linux/interrupt.h:66)
/home/heff/adm8211/adm8211-hw.c:2030: Warning: passing argument 2 of 'request-irq' from incompatible pointer type
/home/heff/adm8211/adm8211-hw.c: in function 'adm8211-80211-header-parse':
/home/heff/adm8211/adm8211-hw.c:2030: error: 'struct sk-buff' has no member named 'mac'
/home/heff/adm8211/adm8211-hw.c:2030: error: 'struct sk-buff' has no member named 'mac'
/home/heff/adm8211/adm8211-hw.c: in function 'adm8211-probe':
/home/heff/adm8211/adm8211-hw.c:2584: error 'struct net-device' has no member named 'get-wireless-stats'
/home/heff/adm8211/adm8211-hw.c: in function 'adm8211-suspend':
/home/heff/adm8211/adm8211-hw.c:2723: error: too many aruments to function 'pci_save_state'

```
Etc etc
```

Make [2] *** [/home/heff/adm8211/adm8211-hw.o] Error 1
Make [1]: *** [/module_/home/heff/adm8211] Error 2
Make[1]: Leaving directiory 'usr/src/linux-headers-2.6.22-14-generic'
Make: *** [modules] Error 2 
```

---

### Post by spiderbatdad on 2007-12-29
how did you try to install? Did you read the install file. Probably need to "make" first then follow instructions.

---

### Post by geekchicohio on 2007-12-30
Per your instructions I'd cd'ed to the directory and done sudo make install to get the errors I showed you. I have also tryed  make and then make modules-install, though the first of those commands resulted in a similar batch of errors to running make install.
There's a mention of an alternate makefile in the install guide in the tarbell, but I don't know how I would use it

I'm not really well enough versed in cli to do a whole lot od troubleshooting on my own.

---

### Post by spiderbatdad on 2007-12-30
that's a real bummer. I hoped that driver would work for you easily. I'll take a look at the files to see what I can see. And I'll check some more if necessary, for an alternative driver.

---

### Post by spiderbatdad on 2007-12-30
its hard to be sure what's going on without seeing the errors resulting from "make"  are there dependencies unmet?  Try installing the build-essential package and running make again.```
sudo apt-get install build-essential
``` I assume you're still on your phone...so I wont ask for a ton of output.

---

### Post by spiderbatdad on 2007-12-30
there has been question in this thread that you have a driver already. just verify with ```
sudo lshw -C Network
``` and look for a "configuration" line in Network 1 of eth0
it should look something like this:

```
 *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:02:3f:09
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
      ** configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.15.100 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s**

```

can you see the part in bold? Especially where the driver is listed.

---

### Post by geekchicohio on 2007-12-30
I installed the package you recommended and re-tried make install. Same errors. I tried running make again and got many errors identical to the ones I posted for make install. Additionally:```

Error: linux/config.h: no such file or directory
'Struct sk-buff' has no member named 'mac'
Too many arguments to pci restore state.
Warning: implicit declaration of function pci module init

``` let me know if you need more.

Also, if you might be willing (and if it's allowed by ubuntuforums) we could try this via email. I could email you photo's taken with my phone's camera of what I'm seeing. I tested this and think it could work, however my phone won't let me attach them to posts here.

---

### Post by spiderbatdad on 2007-12-30
did you see my post just prior to this one, regarding lshw -C Network?

---

### Post by geekchicohio on 2007-12-30
```
*-network:0
Product: nc100 network everywhere fast ethernet 10/100
Vendor: admtek
Physical id: a
Bus info: pci@000:00:0a.0
Logical name: eth0
Version: 11
Serial: 00:12:17:56:92:69
Width: 32 bits
Clock: 33MHz
CapabilitiesF pm bus-master cap-list ethernet physical
Configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 maxlatency=128 mingnt=64 module=tulip multicast=yes

```

There's also ```

*network:1 DISABLED
Description: wireless interface etc. Etc. Etc. I don't have a wifi network in this apartment.
```
So I have a driver? I dunno if this is great news or terrible news, as stumped as I am by all this. But hopefully this helps.

---

### Post by spiderbatdad on 2007-12-30
looks like great news. right click on the network monitor on the panel in the upper right and click "Enable Networking" then left click on the monitor and click "Wired Network."

---

### Post by geekchicohio on 2007-12-30
I've got networking enabled and wired network selected but to no effect.
However, I have another networking icon on a panel that I just found in the add to panel screen. I'm told that the system "could not find indormation on interface 'eth0:avahi' in /proc/net/dev
Maybe this is a clue?

---

### Post by spiderbatdad on 2007-12-30
ok try to manually configure your network by left click on monitor and select manually configure. IDK about your modem or router but assuming you use dhcp it should be simple...its a graphical program. If it fails I think something went wrong with your installation. Maybe boot off the live cd with your ethernet cable plugged in and see if you have network, if you do, I think something went wrong with the installation. Good Luck!

---

### Post by spiderbatdad on 2007-12-30
i noticed much earlier (page 1) you had an error that implied you were missing configuration files as well. I think you should boot from the live cd and see if you have networking...

---

### Post by geekchicohio on 2007-12-30
Hi there,
I've booted from this gutsy live CD and also from a dapper cd I found. No networking. And using the GUI networking settings has been fruitless, failing to succeed at that is what brought me here to start this thread in the first place.

---

### Post by spiderbatdad on 2007-12-30
came across a number of bug reports regarding the tulip driver...how you tried to make any progress with the other ethernet device?

---

