---
title: "Corega Ethernet PCMCIA card won't work"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by maino on 2007-01-09
I have been trying to make a PCMCIA LAN Card work on Ubuntu.
I tried in Dapper, and as it didn't work, I am now trying on Edgy.
The card is a Corega LAPCCTXD.
According to the Corega webpage, it is supposed to use the pcnet_cs driver.
However, according to dmesg, Ubuntu seems to try to use the hostap_cs, which I think is a wireless driver.

The closest thread I have found is this:
[http://www.ubuntuforums.org/showthread.php?t=29092&highlight=corega](http://www.ubuntuforums.org/showthread.php?t=29092&highlight=corega)
but it doesn't seem to be solved.

The information from pccardctl is as follows:

[INDENT]# pccardctl ident
Socket 0:
  product info: "corega K.K.", "(CG-LAPCCTXD)", "(HardwareFirmwareVer.)", "(nothing)"
  manfid: 0xc00f, 0x0000
  function: 6 (network)

# pccardctl info
PRODID_1="corega K.K."
PRODID_2="(CG-LAPCCTXD)"
PRODID_3="(HardwareFirmwareVer.)"
PRODID_4="(nothing)"
MANFID=c00f,0000
FUNCID=6

# pccardctl status
Socket 0:
  5.0V 16-bit PC Card
  Subdevice 0 (function 0) [unbound][/INDENT]

So the device is there and Ubuntu notices, but the driver is not bound.

I tried blacklisting hostap_cs by adding the line
[INDENT]blacklist hostap_cs[/INDENT]
at the end of the file /etc/modprobe.d/blacklist.
But it didn't work.

What am I doing wrong?
I appreciate any directions to get this card working.
Thank you for reading this post, best wishes.

---

### Post by deadgobby on 2007-01-09
It may be the firewire.
Your firewire ethernet connection should be listed under System-> Administration-> Networking, or you can use ifconfig to list your network devices.

---

### Post by maino on 2007-01-09
Wow!  Thank you for the hyper quick response.

I am afraid nothing comes up in System-> Administration-> Networking, or ifconfig.
The listings do not change in them even when I insert (or remove) the card. :(

---

### Post by deadgobby on 2007-01-09
So the card is through USB no????  Can you let the forum know what your system specs are?
GObby

---

### Post by maino on 2007-01-09
Oops, I am sorry.

It is a PCMCIA card, and I am trying to use it on a DELL laptop, Latitude D820.

The output from dmesg when I insert the card is like this:
```
[17181756.668000] pccard: PCMCIA card inserted into slot 0
[17181756.668000] pcmcia: registering new device pcmcia0.0
```

and that's it...

---

### Post by maino on 2007-01-12
I've been searching around for more information, and came up with some tweaks using pcmcia-cs, which is deprecated by pcmciautils that Edgy uses.
I tried installing pcmcia-cs, but couldn't really understand what I should do to get it working instead of the current pcmciautils, and gave up.  I am not even sure it was a good idea to even try.

I also found a faintly related topic on a card ID error in the kernel:
[http://lists.infradead.org/pipermail/linux-pcmcia/2006-April/003457.html](http://lists.infradead.org/pipermail/linux-pcmcia/2006-April/003457.html)
I am wondering if my card has a similar error.
It would involve compiling the driver myself, which I couldn't find much information on.  Lots of information on binary drivers, but none on compiling from scratch.  Well, I suppose you usually don't need to do this kind of stuff.

So I am wondering whether I am running off the track.

Any ideas?

---

### Post by maino on 2007-01-15
I have not been able to fix the problem myself, but I am posting the information I found, hoping it will be some help to someone in the future.

I found some information in the linux-pcmcia mailing list archive.
[http://lists.infradead.org/pipermail/linux-pcmcia/2006-April/003457.html](http://lists.infradead.org/pipermail/linux-pcmcia/2006-April/003457.html)
(Searched with keyword "Corega").

There seems to be some kind of Card ID error.
Although it is supposed to be fixed...
If I understood more, I should probably be recompiling the driver.

---

### Post by serador on 2007-04-05
I have the same card, Corega LAPCCTXD and it works out of the box with Ubuntu 7.04 BETA.

---

### Post by maino on 2007-04-08
Many, many thanks for the information!

I am currently not able to check, hoping it will work.

---

