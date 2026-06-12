---
title: "PCMCIA light on in Xubuntu, but cannot connect to wireless"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by kinson on 2006-12-08
Hi guys,

I've just installed Xubuntu on my laptop(running Ubuntu on the desktop). After a couple of minor hiccups, I managed to boot into the desktop.

I've got a problem here though:

After I've boot into the desktop, I can see that my pcmcia wireless card light(power) is on. When I go into the network settings manager, I can see that my wireless card(eth1) is active, and I've put the correct properties(WEP, DHCP), but it still doesn't connect :( I've set the "default gateway device" to "eth1" already

when I type "iwconfig" i get:

IEEE 802.11b ESSID:"balau" nickname: ""
mode: managed access point: not-associated bit rate:11Mb/s
tx-power: off
etc etc...

I think xubuntu installed pcmciautils and udev(i checked Synaptic).

Another thing I'm curious is that if I'm already logged into the desktop, and then plug in the pcmcia card, the light does not come on, i need to reboot the pc with the card plugged in before its recognized. I thought udev was supposed to take care of this? :-k 

Oh, I've also tried plugging in a pcmcia card with an ethernet jack, doesn't work either :( (but again, the light comes on).

Btw, the wireless card I'm using is smc2635w. If i need to install any drivers, I'm not sure how :( 

Any help would be great :) I realli wanna get it working on me laptop :)

Cheers,
Kinson

---

### Post by grumpymole on 2006-12-08
Kinson,

This is a [good place to start]("https://help.ubuntu.com/community/WifiDocs"), especially [this page]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").  Also, the troubleshooting pages have lots of good stuff about working out whether your card is detected or not.

[This thread]("http://ubuntuforums.org/archive/index.php/t-7972.html") might have some relevant information.

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by kinson on 2006-12-08
Thanks for the reply :)

I typed "lspci -v | less"

and roughly, my network card was:

```
linksys ADMtek ADM8211 802.11b wireless interface (rev 20)
subsystem: standard microsystems corp (SMC) SMC2635W 802.11b wireless lan pcmcia (cardbus) card.
```

So I'm assuming I download with the link for "cardbus" from here: [http://linux-wless.passys.nl/query_part.php?brandname=SMC](http://linux-wless.passys.nl/query_part.php?brandname=SMC)
 and not "pcmcia"? (dunno whats the diff)

I read through a couple of the sites, I think this is the driver I need (??)

[http://aluminum.sourmilk.net/adm8211/](http://aluminum.sourmilk.net/adm8211/)

I downloaded the driver from the bottom, unpacked it, and I didn't know what to do :( I read the "INSTALL" thing, but didn't realli understand the instructions. it said:

> To install, just run make install. You can also do make, then make modules_install, which uses the kernel build system to install the modules. However, if you do it the second way, you'll need to run depmod -a manually.

To put the driver inside the kernel source tree:
1. Apply kernel.patch
2. Copy the entire adm8211 directory into $(KERNEL_SOURCE)/drivers/net/wireless

Then you can configure/compile/install the driver like any other driver included with the kernel. Note that the driver is installed to a different place (as a module) than usual when compiled & installed inside the kernel tree, so be careful when upgrading.

To load the driver if it isn't automatically loaded, just run modprobe adm8211.

I don't understand what it means by run make install. Sorry, I'm totally n00b about this :(

Any idea? :|

Thanks :)
Kinson

---

### Post by grumpymole on 2006-12-10
Kinson,

EDIT: Looking at [another post]("http://www.linuxforums.org/forum/150847-post3.html"), it looks like there should be an adm8211 driver included.  Open a commandline and type ```
lsmod
``` and look for adm8211 in the output.  If it is there, you shouldn't have to do all the compilation stuff.  If it isn't, then try ```
sudo modprobe adm8211
``` and see what the response is.

----- END OF EDIT -----

At the command line, type ```
make install
```  If you get a message saying something like "make not found", then you need to install the build-essential package.  To do this, ```
sudo apt-get install build-essential
``` at the commandline.

Unfortunately, some wireless cards don't just work out of the box and require a bit of commandline intervention.

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by kinson on 2006-12-14
Hi Warren,

Yeah, I understand some of these wireless cards don't just work outta the box, thats why I'm happy to get some help around here :D Everybody's been realli great so far anyways :D

Anyways, I did "lsmod | grep adm", it returned this:

```

kinson@xubuntu:~$ lsmod | grep adm
adm8211                58112  0

```

Does this mean that the drivers are already installed, and I don't need to go through that make install thingy?

I tried the "make install" command earlier, and it said something like command not found. So right now I've installed the "build-essential" thing, and "make install" doesn't say "command not found" anymore.

But where do I go after that? I'm quite lost to be honest :P

Funnily enough, the PCMCIA card for the ethernet port doesn't work either...:confused: The light lights up as well(it needs to be plugged in before boot in order to work). I would suspect that the pcmcia slots weren't working, but they were working in windows xp before I formatted, so I think they're working :(

Another thing, this laptop isn't in the best working condition, its just for me to learn more about xubuntu/ubuntu, and hopefully help me on the road :p But I've been encountering some other problems as well.

1) system freezes randomly (onli in xubuntu) (is there any logging that I may post in another thread?)
2) "sudo shutdown -h now" proceeds in the shutting down screen where its shutting down the processes one by one, and hangs there.. :(

Anyways, those 2 are topics for another thread, but its just off the top of your head :P

I'm hoping to get this pcmcia issue solved(main issue), cause without being able to connect to the internet, its a bit hard to update/learn stuff for a noob like me :p

Cheers,
Kinson

---

