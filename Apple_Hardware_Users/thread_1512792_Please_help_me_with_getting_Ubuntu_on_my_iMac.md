---
title: "Please help me with getting Ubuntu on my iMac"
date: 2010-06-18
forum: Apple Hardware Users
---

### Post by c-a-b on 2010-06-18
My Hardware: 
iMac G5 20", 2.0 GHz PPC G5 single processor, 2 GB DDR SDRAM, ATI Radeon 9600 AGP with 128 MB VRAM, 250 GB Maxtor Harddisk, PIONEER DVD-RW Superdrive.

I figured out partitioning the hard drive with 30 GB of ext3 space at the end of my disk. Then I started a Ubuntu 6.~ Live DVD and managed booting from it. 

Booting is a major problem itself with several Ubuntu CDs I have, from Ubuntu 6.~ to 10.04 nightly built for PPC I have several CDs to try. Few of them are running at all and most of them only if the iMac had some time completely off power before. Sometimes it gets til "type what you want to do", sometimes it gets til Installer, sometimes it gets to Live, but mostly it hangs somewhere between. 

When I got to that point I can install, wheter live or not, it hangs either on partitioning tool (Ubuntu 8+9+10 versions) or it might get until the partitioning tool (6.~) but then... it refuses the partition I want them to give and says something about "root system failed, please select with partitioning tool", even when I try the automatic mode with "use biggest free space" and so on. With manual partitioning I don't get it what to do. 

I really would like to use Ubuntu, 10.04 for the best, additionally to MacOS X on this iMac but it's really tough work. :(

---

### Post by phildini on 2010-06-18
For the partitioning, google a tool called iPartition. I believe they have a free version, and it really is the best tool out there. There might even be a partitioning tool on your MacOS install disks, depending on the version. Partition the disk using that disk, and then try the Ubuntu install.

As for the weird boot issues, I've never run iuto that issue, but it seems like there is some hardware issue that is preventing correct operation. I believe the Ubuntu LiveCD has boot-time options for turning off lots of extras. Try messing with those?

---

### Post by psy-man on 2010-06-18
strange you are having problems with several cd's. 
Did you check the md5 checksum of the images?
                                               Sorry I can't advise how to do that on OSX, burnt my iso's on a ubuntu pc
Did you burn them at the slowest speed?

I did have trouble with  live CDs on my old G3  as the video settings in the live system are not compatible with my monitor, it goes out of range,  the system seemed to hang, but really it  just took a long time to load. I left it running and went for a long walk, when I came back there was a live ubuntu desktop waiting for me.

---

### Post by c-a-b on 2010-06-19
Thank you!

I managed partitioning with MacOS X Install DVD and then converted the 30 GB Disk into ext3 for Linux. But after that, sadly, I wasn't able to say Ubuntu to select that free disk and use it for repartitioning and whatever it likes. 

OK I can try to burn another CD with slower speed...

---

### Post by psy-man on 2010-06-19
checking md5sums and that on macOSX at the bottom  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The partitioner in ubuntu will probably not like the Mac formated ext3 partition and want to re format it.
Best use the Mac partioner to resize the MacOS partition and leave the rest of the disk as unused space then the ubuntu partitioner will see this as available for use. Either way make sure you check the integrity of your Ubuntu DVD/CD.

Also I might add that I have had a much more rewarding experience with  install CDs rather than live CDs. Even though the gui is basic, as long  as you read and understand the options and are prepared to have a couple  of goes to get it right.  The Debian Lenny PPC install CD1 works like a  charm for me. 

I had a great deal of trouble persuading my G3 to boot from a non Mac  CD. Holding down the c key, resetting the pram (Command+Option+P+R) all  to no effect. In my case the only thing that worked was removing OS9 by  plugging in a different hard drive. Now I know that this is not an easy  thing to do with an imac. So before continuing..
Ask yourself the following
 Can you afford to mess up your existing Mac OS? If No stop now.
 Have you backed up any vital data to external media ? If No, do it now!
Can you reinstall Mac OS if it gets messed up or if you don't like  Ubuntu? If No, stop now

(I have Mac OSX running on a G3 imac, It looks very much like a unix  system. More Refined and slick than Ubuntu. It runs smoothly on the  machine dispite the relatively slow 333mHz cpu. The only thing it  doesn't do well is play flash media, "slide show utube" now as far as I  know (which isn't much) the flash media problem is an issue of  architecture which running Ubuntu or Debian or any other linux OS is not  going to solve.)


So if you have OSX why try and add Ubuntu? 

OSX is fool proof but you pay a price.

Linux is powerful but can be daunting and dangerous.  Ubuntu and Debian  is Linux made easy, but neither are fool proof.

If it is a matter of being able to use the excellent and free software  in the Ubuntu/Debian repository, and benefit from the support of  the  forum communities.
If you understand the consequences of your actions, Why not take the  leap and dump Mac OS.

---

### Post by c-a-b on 2010-06-19
Yay, I did it well! 

Finally Ubuntu 10.04 PPC is on my PC iMac G5! The only problem was to find a CD that was *good enough* for my iMac to fiddle Data out of it on my iMac! All other CDs I've burned seem to be stinkers. 

Now I've installed Ubuntu 10.04 effortlessly on my iMac. The only problems: 

1) Wireless Network won't work. :(
2) Desktop effects aren't running better than "standard". 

While having no WLAN on Ubuntu the driver update might be a hassle? 

Ideas? :)

---

### Post by linuxopjemac on 2010-06-19
what kind of wireless card do you have ?

---

### Post by c-a-b on 2010-06-19
> **linuxopjemac said:**
> what kind of wireless card do you have ?

AirPort Extreme, Broadcom BCM43xx 1.0

---

### Post by linuxopjemac on 2010-06-19
can you do the following:
```
lspci -vnn | grep 14e4
```

---

### Post by c-a-b on 2010-06-19
Where do I have to do that?

---

### Post by linuxopjemac on 2010-06-19
what do you think about Linux in a terminal?

---

### Post by goldshirt9 on 2010-06-19
you type it in a 
Terminal

---

### Post by c-a-b on 2010-06-19
> **linuxopjemac said:**
> can you do the following:
```
lspci -vnn | grep 14e4
```

I can. lspci -vnn gives an overview on all hardware. grep 14e4 shows no reaction. 
What of these things do you want to read?

---

### Post by c-a-b on 2010-06-19
Broadcom Cooperation BCM4318 (AirForceOne 54g)
(...)
Kernel Driver in Use: b43-pci-bridge
Kernel Modules: ssb
:confused:

---

### Post by linuxopjemac on 2010-06-19
try and paste the output here pls

```
lspci -vnn | grep Broadcom
```

---

### Post by linuxopjemac on 2010-06-19
ok Broadcom 4318. You need the b43 driver. Do the following:

```
sudo apt-get install b43-fwcutter
```

This will extract the firmware out of your Broadcom card and it will put it in /lib/firmware.

If you see that it extracts the firmware, you have to reboot and it will work.

---

### Post by c-a-b on 2010-06-19
> **linuxopjemac said:**
> try and paste the output here pls

```
lspci -vnn | grep Broadcom
```

Cut and paste isn't that easy without internet connection. ;) 

> ok Broadcom 4318. You need the b43 driver. Do the following:

sudo apt-get install b43-fwcutter
This will extract the firmware out of your Broadcom card and it will put it in /lib/firmware.

If you see that it extracts the firmware, you have to reboot and it will work.

Thank you, I'll try! :)
--> Didn't work because no Internet connection, packages cannot be loaded. :( 

Next issue is hibernation and stand-by. It don't awake after sleeping, whatever I try. 
Also strange: Restartin now didn't ask for MacOS X or Linux, it booted Ubuntu directly?

---

### Post by c-a-b on 2010-06-19
Goin on System Menu > Administration > Hardware Drivers shows that "Broadcom B43 Wireless Driver" is available for Activation, but it too has to be loaded from an Internet Adress. 

Meanwhile there is no networking at all left. Clicking on the WLAN symbol right above, there is only "networking disabled".

---

### Post by linuxopjemac on 2010-06-19
connect it with a cable for the time being.

---

### Post by c-a-b on 2010-06-19
> **linuxopjemac said:**
> connect it with a cable for the time being.

Even with cable there's no connection. :(

---

### Post by c-a-b on 2010-06-19
Another try. Booted from Ubuntu_PowerPC_lucid CD and selected option "install drivers". OK, ist started Live mode and installed drivers for LAN connection, WLAN failed. 

Then, in Live mode, Internet over LAN worked, but WLAN not. 

Restarting in Ubuntu without CD there were no changes. Didn't work either in LAN nor in WLAN. No drivers there. 

In Ubuntu no inserted CD was to see. 

:confused:

How can I get drivers from the CD when the CD isn't available? What can I do? :(

---

### Post by linuxopjemac on 2010-06-19
when you boot into Ubuntu form the hard disk, try to do the following:

make sure you have the following in /etc/network/interfaces (I assume you get an IP address via your router:

```
auto eth0
iface eth0 inet dhcp
```

To check it do:

```
sudo nano /etc/network/interfaces
```

if you are ready:
CTRL-X and "y" to save

Then:

```
sudo ifdown eth0
sudo ifup eth0
```

You should be connected by cable now...

---

### Post by c-a-b on 2010-06-20
> **linuxopjemac said:**
> when you boot into Ubuntu form the hard disk, try to do the following:

make sure you have the following in /etc/network/interfaces (I assume you get an IP address via your router:

```
auto eth0
iface eth0 inet dhcp
```

The file contained following:
```
auto lo
iface lo inet loopback
```

> To check it do:

```
sudo nano /etc/network/interfaces
```

if you are ready:
CTRL-X and "y" to save

Didn't save anything. 

> Then:

```
sudo ifdown eth0
sudo ifup eth0
```

You should be connected by cable now...

Sadly, I'm not. :( Console said:

```
ifdown: interface eth0 not configured.
...
Ignoring unknown interf eth0=eth0
```

---

### Post by linuxopjemac on 2010-06-20
You should add these lines I gave you to /etc/network/interfaces

It will in total look like this:

```
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp
```

edit the file with nano:

sudo nano /etc/network/interfaces

add the lines and save:
CTRL-X and "y"

Then do the ifdown ifup commands

---

### Post by c-a-b on 2010-06-20
Thank you... I did so but... there's still no network. :(

i even cannot save this console text to copy it. usb-stick is read-only for ubuntu. so i have to type it *argh*

```
chris@ubuntu:~$ sudo nano /etc/network/interfaces
sudo: password for chris: 
chris@ubuntu:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
chris@ubuntu:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For Info, please visit https://www.isc.org/software/dhcp

Listening on LPF/eth0/00:11:24:db:91:d6
Sending on LPF/eth0/00:11:24:db:91:d6
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCFOFFER of 192.168.2.107 from 192.168.2.1
DHCPREQUEST of 192.168.2.107 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.107 from 192.168.2.1
chown: failed to get attributes of `/etc/resolv.conf´ : No such file or directory
chmod: failed to get attributes of `/etc/resolv.conf´ : No such file or directory
bound to 192.168.2.107 -- renewal in 148213 seconds.
chris@ubuntu:~$

```

Hope thats somewhat useful for you.

---

### Post by linuxopjemac on 2010-06-20
It looks like you have an IP address assigned (192.168.2.107). You don't have internet (yet) as you don't have a nameserver set. Normally this shouldgo automatically

Add the following lines to /etc/resolv.conf

```
nameserver 192.168.2.1
```

with:

```
sudo nano /etc/resolv.conf
```

save with
CTRL-x and "y"

---

### Post by c-a-b on 2010-06-20
Thank you I'll try soon after Lunch. 

By the way, when I start from Live CD, there is ethernet connection and I can load the broadcom driver. Is there any chance to get that to the installed linux? Or a chance to reinstall with all new drivers and updates included?

Edit: Nameserver already existed in /etc/resolv.conf

---

### Post by c-a-b on 2010-06-20
I remember that eht0 network was available yesterday after installing ubuntu. wlan was also there but with wrong driver so it dign't work. i think problems began after ubuntu set itself into a sleep mode that didn't work correctly, fans didn't stop and the imac was somewhat still active. i couldn't awake it anymore with mouse and keyboard so i had to press power. 

since then, there are problems with ethernet and wlan. and cds don't show up on desktop.

---

