---
title: "Ndiswrapper vs. Pre-Installed Wireless Drivers"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by MartinB101 on 2007-07-29
My first post.  There is an ocean of stuff on Ndiswrapper and wireless around but I'm lost on the ocean :(  I found one post where my problem was almost addressed by "kevdog":
[http://ubuntuforums.org/showthread.php?t=483548&highlight=ndiswrapper]("http://ubuntuforums.org/showthread.php?t=483548&highlight=ndiswrapper")
However, this is marked "SOLVED" for the lucky poster and I didn't want to add.  Also, "Absolute Beginner" is a far better description of my status :)  Anyway, the problem.

Wireless did not work "out of the box".  I found the correct Windows driver (prisma00).  Using kevdog's instructions, I have a clean install of Ndiswrapper and  I successfully installed the drivers with Ndiswrapper.  However, when I do this:
[B]martin@martin-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: a
       bus info: pci@00:0a.0
       logical name: wmaster0
       version: 01
       serial: 00:60:b3:1e:5a:9f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=prism54pci latency=80 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d0000000-d0001fff irq:20[/B]
it shows the driver "prism54pci" being used.  From kevdog's post, I assume this is the original, supplied driver.  I don't have wireless connectivity.

Also, when I do this:
[B]martin@martin-laptop:~$ sudo iwlist scan
Password:
lo        Interface doesn't support scanning.:confused:

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning : Operation not supported

wlan0     No scan results[/B]
no network is found, even though I'm sitting next to the router and the missus is using it on her laptop downstairs:confused:

I'm now completely lost:(

I've got Ubuntu (7.04) doing everything else I need and I don't want to be be beaten by this.  Any help towards what I do next would be very gratefully received.

Cheers

Martin

---

### Post by yorkie on 2007-07-29
I think wireless  connection should be eth01 eth0 is ethernet port  try scanning with eth01

---

### Post by IamAcoconut on 2007-07-29
Someone please correct me if I'm wrong, but I think "driver=" should point to ndiswrapper if it was used to install a windows driver.
Try this:```

sudo rmmod ndiswrapper
sudo rmmod prism54pci
sudo modprobe ndiswrapper
lshw -C network
```

---

### Post by ugm6hr on 2007-07-29
Before using ndiswrapper - I would suggest trying Wicd first.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
[http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq)

It does mean removing Network Manager from Ubuntu (network-manager and network-manager-gnome in Synaptic) though.

The prism54pci driver is indeed the native linux one - and it seems to behave in an unusual fashion, but I got my PCMCIA prism54 card working with it and Wicd (albeit with incorrect wifi strength references, and Wicd connecting, but not recognizing the connection).

Have a read of my progress with it here (username same as here), if you are interested:
[http://wicd.sourceforge.net/phpbb/viewtopic.php?f=5&t=131&st=0&sk=t&sd=a&sid=23cc9cab1c842eabc99b87ff1deec08e&start=10](http://wicd.sourceforge.net/phpbb/viewtopic.php?f=5&t=131&st=0&sk=t&sd=a&sid=23cc9cab1c842eabc99b87ff1deec08e&start=10)
I will be trying the previous v1.2.9 again soon, to see what the problem is (perhaps you might like to try it too).

---

### Post by MartinB101 on 2007-07-29
> **yorkie said:**
> I think wireless  connection should be eth01 eth0 is ethernet port  try scanning with eth01
Thanks, yorkie.  As far as I can tell, eth0 is my ethernet connection, which is working fine.  wlan0 and wmaster0 both seem to be related to wireless.  Only wlan0 seems to be activated for scanning and that can't find any networks.  Sorry if I've missed your point.  I really am new at this.

Cheers

Martin

---

### Post by ugm6hr on 2007-07-29
> **MartinB101 said:**
> Thanks, yorkie.  As far as I can tell, eth0 is my ethernet connection, which is working fine.  wlan0 and wmaster0 both seem to be related to wireless.  Only wlan0 seems to be activated for scanning and that can't find any networks.  Sorry if I've missed your point.  I really am new at this.


That's right - wlan0 is your wifi.  For some reason iwlist scan returns No scan results on my prism54 too - but Wicd works anyway.  Don't know how!

---

### Post by imdano on 2007-07-29
^That really is the strangest thing.  No idea how it's managing to populate the list of wireless networks, all wicd does is ifconfig <wireless interface> up, then iwlist <wireless interface> scan, then parse the result.

---

### Post by MartinB101 on 2007-07-29
> **IamAcoconut said:**
> ...  I think "driver=" should point to ndiswrapper ...
Thank you.  I am now using ndiwrapper+prisma00 as the driver.  However,  I still can't detect any networks.  Any further help appreciated

Ugm6hr  -  Since I am one step further forward with ndiswrapper, I'll stick with that for now and come back to wicd, if necessary.  I don't want to try too many things at once but thanks for your suggestion

Cheers

Martin

---

### Post by IamAcoconut on 2007-07-29
> I'll stick with that for now and come back to wicd, if necessary. I don't want to try too many things at once but thanks for your suggestionYou got it wrong, Martin. Wicd is no driver, it's just a replacement for network-manager and wifi-radar. Feel free to install it and see if it works.

And important thing - since it's beginner-talk - once you reboot you'll have to replace native driver with ndiswrapper again, unless you make these changes permanent by adding an entry for ndiswrapper in modules ```
sudo gedit /etc/modules
```
And one for prism54pci in blacklist 
```
sudo gedit /etc/modprobe.d/blacklist
```

---

### Post by MartinB101 on 2007-07-30
> **IamAcoconut said:**
> You got it wrong, Martin. Wicd is no driver, it's just a replacement for network-manager and wifi-radar....
Not for nothing am I posting as an Absolute Beginner :)  I'm not in front of my Linux machine, at present, but I'll try it and report back.  Thanks to all for the help.

Cheers

Martin

---

