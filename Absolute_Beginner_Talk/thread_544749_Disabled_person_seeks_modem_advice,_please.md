---
title: "Disabled person seeks modem advice, please"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by jharadie on 2007-09-06
Hi,

I'm asking for help about modems.

The technical stuff: Microtel desktop, AMD Semprom 1.6G processor, 768M RAM, Feisty 7.04.  No serial port.  Multiple USB ports, 2 already running webcams.

I think it has an ISA slot; someone gave me an old Digicom/Creative Modem Blaster V.90 56k Data/Fax with Voice.  Will that work easily with Ubuntu?

I've got a couple PCI modems (Conexant) laying around, but the configuration stuff is way over my head and really freaks me out.

I'm willing to buy a USB modem if I can find one that will easily work with Ubuntu.  I just would like it to be fax and caller-ID capable.  The cheaper the better (thanks to my limited income).

All advice and recommendations are appreciated.

My disabilities won't let me do hardware-type work for very long, and severely limit me from doing complicated software stuff (like trying to get a Conexant PCI modem to work).  But *I'M NOT* going back to Windoze unless there is absolutely no other choice! :)

Thanks.

It might help if I clarify what I'm doing.  I plan to use the modem for outbound fax.  Also, if I can get cheap modems on eBay, I'll get two.  The other will be attached to a QEMU'd Win98 virtual, running a special program I use (related to some of my disabilities), a program that's not yet available in Linux.

:)

---

### Post by p_quarles on 2007-09-06
I've never tried to configure a dial-up modem in Linux, but I'll share what I know:

There are basically two kinds of modems: software modems (the internal ones, usually) and hardware modems. Software modems are generally sold in OEM systems, and are quite frequently will only work with the preinstalled software. Hardware modems *typically *have much better support in Linux.


I don't know whether the Digicom modem will work, but plugging it in is the easiest way to find out. You might need to install the gnome-ppp package before it works.

Conexant modems are among the few software modems that have a Linux driver. The driver is proprietary, but you can download and run the trial version for free, to see if it works for you:
[http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)

Hope this helps.

---

### Post by jharadie on 2007-09-06
Thanks for the info.  Unfortunately, the Conexants I have must be so old, they're not listed under the recognized PCI ID's at that site.

I'm going to wait a bit before trying to plug in that ISA modem (if there is an ISA slot).  My disabilities are such that it's an almost 2 hour job to move out the comp, remove the side panel, plug it in, put everything back. :(

Thanks again.

---

### Post by p_quarles on 2007-09-06
If it's convenient, you might still give the Linuxant driver a try. I just read their compatibility list, and it says that some Conexant-based modems are shipped with different PCI IDs. In other words, yours might still work, they just haven't tested it specifically. 

Also, I just found the following site, which keeps tracks of which modems work with Linux. A lot of info there:
[http://xmodem.org/](http://xmodem.org/)

---

### Post by oilchangeguy on 2007-09-06
does the computer have a network card, if not they're cheap. usually around 10.00. and if you're spending alot of time in front of the computer i'm sure you'd be much happier with a highspeed connection. if price is the issue, most phone and cable companies now offer entry level packages. with prices at or very near that of dial-up. but with speeds that will blow away dial-up. if highspeed is available in your area, you owe it to yourself to check pricing.

---

### Post by jharadie on 2007-09-06
> **oilchangeguy said:**
> does the computer have a network card, if not they're cheap. usually around 10.00. and if you're spending alot of time in front of the computer i'm sure you'd be much happier with a highspeed connection. if price is the issue, most phone and cable companies now offer entry level packages. with prices at or very near that of dial-up. but with speeds that will blow away dial-up. if highspeed is available in your area, you owe it to yourself to check pricing.

I'd like to, but being disabled I live on a limited income, and not even the intro rates are within reach.  Society has not yet caught up with technology insofar as compelling providers to make allowances for low income people, as they have with telephone service, for example.  Nowadays, basic telephone service is considered a necessity not a luxury, and most states (and Medicaid) require providers to make allowances so low income people can afford it.  Internet is still considered a luxury (if only it would be realized how many disabled people rely on it for so many things!), so many low income users are forced to continue using modems, and by extension, forced to continue using Windoze.  *sigh*  The day will come when this situation will change, and I will be ready with a stack of Ubuntu CDs to hand out! :)

---

### Post by p_quarles on 2007-09-06
> **jharadie said:**
> I'd like to, but being disabled I live on a limited income, and not even the intro rates are within reach.  Society has not yet caught up with technology insofar as compelling providers to make allowances for low income people, as they have with telephone service, for example.  Nowadays, basic telephone service is considered a necessity not a luxury, and most states (and Medicaid) require providers to make allowances so low income people can afford it.  Internet is still considered a luxury (if only it would be realized how many disabled people rely on it for so many things!), so many low income users are forced to continue using modems, and by extension, forced to continue using Windoze.  *sigh*  The day will come when this situation will change, and I will be ready with a stack of Ubuntu CDs to hand out! :)
I agree with you: internet access shouldn't be a luxury item. A couple years ago, it looked like the free municipal wi-fi movement was gaining ground, but that's now collapsing. My city, Chicago, cancelled its plans for such a network on the grounds that internet access is already affordable for everyone(!). It doesn't take a genius to figure out that's just not true.

Anyway, be sure to take a look at the link in my previous post. You might be able to use that database to find a good external modem that will work with Linux, and then find a cheap one on Ebay or something.

---

