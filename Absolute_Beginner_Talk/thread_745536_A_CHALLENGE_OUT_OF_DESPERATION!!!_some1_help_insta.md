---
title: "A CHALLENGE OUT OF DESPERATION!!! some1 help install my 7.10.....please.............."
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by dariusdwtt on 2008-04-04
Where shall I begin...oh where???

Towards the beginning of last year, I got my first copy of Ubuntu, and boy was I excited,
downloaded, verified burn, md5summed,etc. Popped it in and watched the little orange bar.......
Everything was great but when it came time for lights camera and action, I just had a black screen :(
Prob tried 6 disks, can't remember, tried multiple boot options but still nothing.

So I started my research :)

I found out that the graphics chip on my motherboard was not supported. What a bummer!
And I'd just bought the computer. Couldn't even get 800x600x16.

So I was sad like a pet had died, and of the cds went into the dustbin, but one I stuck in a drawer somewhere?          :-({|=

_________________________________________________________________________________



Some time has passed since then and while cleaning my room a couple weeks ago I found the cd :)

Looked at it and thought, "This doesn't work" and threw it away.

Then one night in front of my computer on the internet, a couple days after, it popped back into my head and I wondered.......

Had a look about and noticed that my motherboard was supported.

So once again downloaded, md5summed, verified etc. Tried live but nothing, just a blank screen after the boot, so I tried all the boot options my limited knowledge could muster, to no avail!

Then got clever :)

Got the alternate cd ( Ubuntu 7.10 64bit alternate ) and installed in text mode with the intention of then installing the openchrome drivers with apt-get. Only problem was apt-get doesn't work!!!!!!

I'm now clueless, and would desperately like to have Ubuntu on my PC.

Could anyone please help me fix apt-get, then fix my display driver, and finally upgrade from text mode to normal desktop Ubuntu if something like that is necessary.

Yours
Darius              :-({|=

_________________________________________________________________________________

What follows are my specs and all my tinkering to date, which has been laborious to say the least, considering I have no idea what I'm doing.

OS: Dual Boot: Windows XP Home 2002 with Service Pack 2
                         Ubuntu 7.10 Gutsy Gibbon 64bit alternate cd text mode

CPU: Intel Pentium 4 3GHz, 256Mb DDR2.

BIOS: Award

Motherboard: Jetway

Model Name: P4M9MP
FSB 1066Mhz LGA 775 Core 2 Duo CPU
2 DDRII 533
VIA P4M890 + VT 8237R Plus Chipset     ([http://www.openchrome.org](http://www.openchrome.org))
Onboard VGA / AC'97 6-Ch Audio
1 PCI-Ex16 / 1 PCI-Ex1 / 8 USB2.0
2 32-bit PCI / LAN / SATA RAID / Micro ATX

Monitor: 17" LG 710S on VIA/S3G Unichrome PRO IGP

Display Properties: 1024x768, DPI 96, refresh 75Hz, Hardware acceleration=none.

Adapter: Chip=VIA/S3G Unichrome Pro IGP, DAC=Internal, Memory=64MB, Bios Info=98.A0.00.02, Driver Version=6.14.10.283

HDD: 80Gb SATA ST380211AS Seagate

DVD-RW: BenQ Light Scribe

MODEM: Mega 100WR (Must be supported, prob the most common modem in South Africa, supplied by Telkom SA)

_________________________________________________________________________________


**_[SIZE="3"]apt-get error:[/SIZE]_**

Many of these with different file names at the end.

```
Failed to fetch http://archive.ubuntu.com/ubuntu/bla/bla/......../bla/Sources.gz
Could not resolve 'archive.ubuntu.com'
Reading package lists.....Done
E:Some index files failed to download, they have been ignored, or old ones used instead.
root@_____:~#_
```

/etc/apt/sources.list    =  Perfect
/etc/hosts                    =  2 lines local host and me, tried entering IP for source manually,                         
                                                       doesn't work.
sudo apt-get clean       =  does nothing
/etc/resolv.conf           =  Nameservers                10.0.0.2

```
ifconfig

lo  Link  encap:Local  Loopback
    inet addr:127.0.0.1  Mask:255.0.0.0
    UP LOOPBACK RUNNING   MTU:16436  Metric: 1
    RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
    Tx Packets:0 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0
    RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)


# ping -c 5 www.google.com
unknown host

# ping -c 5 64.233.167.99
network is unreachable

# netstat -nr
(does nothing)

# cat /etc/network/interfaces
# loopback
auto lo
iface lo inet loopback
# primary
auto eth0
# iface eth0 inet dhcp

# cat /etc/hosts
127.0.0.1 local host
127.0.1.1 Darius
# The following .........etc.
::1      ip6 - localhost  ip6 - loopback
fe00 0 ip6 - localnet
ff00  0 ip6 - mcastprefix
ff02  1 ip6 - allnodes
ff02  2 ip6 - allroutes
ff02  3 ip6 - allhosts

# dpkg  --get -selections tcpdump
install

# sudo vi /etc/modprobe.d/aliases       ( tiny vim won't let me edit )
alias net-pf-10 ipv6
```


[SIZE="3"]**_For display I want to use:_**[/SIZE]


```
# sudo apt-get build-dep xserver-xorg-video-via

# sudo apt-get install subversion autoconf automake1.9 libtool

# svn checkout http://svn.openchrome.org/svn/trunk openchrome

```

_________________________________________________________________________________


Any assistance in said regard would be deeply appreciated       


Darius                                    :-({|=:-({|=

---

### Post by Tomatz on 2008-04-04
Your best off downloading 8.04 beta

[http://www.ubuntu.com/testing/hardy/beta](http://www.ubuntu.com/testing/hardy/beta)

Also i would suggest you use the i386 version over the x86 64 version as its much better supported. This is just my opinion based on personal experience :)

---

### Post by wolfen69 on 2008-04-04
get the daily build of Hardy instead. it will save you alot of time with updates. [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by dariusdwtt on 2008-04-04
could anyone give a quick suggestion regarding uninstalling the one I have now?

---

### Post by Tomatz on 2008-04-04
> **dariusdwtt said:**
> could anyone give a quick suggestion regarding uninstalling the one I have now?

Just reformat during the installation process :)

---

### Post by dariusdwtt on 2008-04-04
quote   384MB of RAM to install from this CD    unquote

---

### Post by sdowney717 on 2008-04-04
you can always painlessly try wubi

[http://wubi-installer.org/](http://wubi-installer.org/)

It is ubuntu hardy and runs in a folder on a windows partition.
It works fine, I put it on my daughters IBM.
just boot windows, got to the site, download installer and install it as an app in windows.
It will use the windows bootloader, so you get a menu to choose booting ubuntu or windows. 
And you can easily uninstall it.

---

### Post by Tomatz on 2008-04-04
> **sdowney717 said:**
> you can always painlessly try wubi

[http://wubi-installer.org/](http://wubi-installer.org/)

It is ubuntu hardy and runs in a folder on a windows partition.
It works fine, I put it on my daughters IBM.
just boot windows, got to the site, download installer and install it as an app in windows.
It will use the windows bootloader, so you get a menu to choose booting ubuntu or windows. 
And you can easily uninstall it.

I wouldn't recommend this as it decreases hdd performance but it might get around your lack of ram.

---

### Post by wolfen69 on 2008-04-04
> **dariusdwtt said:**
> quote   384MB of RAM to install from this CD    unquote

that is for the live cd. you can choose install without going to the desktop.

---

### Post by dariusdwtt on 2008-04-04
wubi says not enough ram....

---

### Post by Tomatz on 2008-04-04
> **dariusdwtt said:**
> quote   384MB of RAM to install from this CD    unquote

Model Name: P4M9MP
FSB 1066Mhz LGA 775 Core 2 Duo CPU
2 DDRII 533
VIA P4M890 + VT 8237R Plus Chipset ([http://www.openchrome.org](http://www.openchrome.org))
Onboard VGA / AC'97 6-Ch Audio
1 PCI-Ex16 / 1 PCI-Ex1 / 8 USB2.0
2 32-bit PCI / LAN / SATA RAID / Micro ATX

**^if that is what you have i dont see the problem in using the live cd???**

---

### Post by dariusdwtt on 2008-04-04
thanks Wolfen69
downloading now

---

### Post by dariusdwtt on 2008-04-04
CPU: Intel Pentium 4 3GHz, 256Mb DDR2.                  (available ram)

BIOS: Award

Motherboard: Jetway

Model Name: P4M9MP
FSB 1066Mhz LGA 775 Core 2 Duo CPU
2 DDRII 533                                                    (slots on motherboard)

---

### Post by dariusdwtt on 2008-04-05
Downloaded...
md5sum failed...
Read verify failed...
live cd check...
Passed!

Thought must be wrong md5sum because it is a daily build? and the bad part of the disk is prob a less important part?

So I installed anyway and WORKS LIKE A CHARM!!!

Thanks Wolfen!

One gripe tho...

Can't change display driver, the one I should be using Unichrome, gives terrible results as with Xorg and S3. So not sure which driver to use? Shows Vesa being used.

Monitor has flicker...

---

