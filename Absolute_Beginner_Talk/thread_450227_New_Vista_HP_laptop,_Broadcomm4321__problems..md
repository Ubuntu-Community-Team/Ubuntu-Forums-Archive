---
title: "New Vista HP laptop, Broadcomm4321  problems."
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by theotherjoey on 2007-05-21
Okay, last month I bought an HP Pavilion  dv6000 with Windows Vista Basic, an AMD Sempron 3500+ processor (which I think is x86). And I found that I hate Vista, so combined with many recommendations I decided to switch.

So,  I've installed Kubuntu Feisty, and have been trying for weeks to get my wireless to work. I believe I have a Broadcom 4321AG miniPCI adapter, but Ubuntu detects it as being a 4328, so one of us is wrong.

I've tried running ndiswrapper using a number of different drivers, including [sp33008.exe]("ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe"), a Dell driver that supposedly worked with the 4328 ([R140746.EXE]("http://ftp.us.dell.com/network/R140746.EXE")), and the Vista driver that come with the computer [sp34488.exe]("ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34488.exe")).

The first two gave me "invalid driver!" errors and failed to detect the hardware at all. The last one detected the hardware but when I ran modprobe there was no effect at all and all I get from iwconfig is:

"eth0: no wireless extensions


eth1: no wireless extensions"

with no mention of "wlan0".

Can anyone help me at all?

FYI, I'm on the wireless in Windows right now, so I can't get my actual logs up.

---

### Post by Kobalt on 2007-05-21
I would suggest you to adapt [this]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29") method with your drivers. This is how I got my broadcom card, also on a HP dv6000, to work.

---

### Post by mongooseman1128 on 2007-05-21
Yes sempron is x86, and if you really want to know what chip you have, open up the RAM cover. In HP the wireless card is right by the RAM. If you have trouble identifying it (you could if your computer also has a bluetooth card) itss the card with a sticker on it that says it's MAC address. this sticker may be covered by another sticker.

---

### Post by theotherjoey on 2007-05-23
> **Kobalt said:**
> I would suggest you to adapt [this]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29") method with your drivers. This is how I got my broadcom card, also on a HP dv6000, to work.
Kobalt, thanks....but that is exactly what I did, and it worked up until Step 7 with the Vista driver, but only that far. It still didn't detect my card. :/

---

### Post by theotherjoey on 2007-05-23
> **mongooseman1128 said:**
> Yes sempron is x86, and if you really want to know what chip you have, open up the RAM cover. In HP the wireless card is right by the RAM. If you have trouble identifying it (you could if your computer also has a bluetooth card) itss the card with a sticker on it that says it's MAC address. this sticker may be covered by another sticker.
Okay, I did that. For some reason ndiswrapper is detecting it as the wrong card. The bottom of the card read BCM94321 (rev 01).

Now I'm really confused, but at least I have an idea of why it's not working.

I'm on wired Internet now so if someone can help I will be very grateful.

---

### Post by Bachstelze on 2007-05-23
```
lspci -n | grep $(lspci | grep Broadcom | awk '{print $1}') | awk '{print $3}'
```

what gives ?

---

### Post by Adler on 2007-05-24
Hi All,

WiFi has driven me crazy!

I have a Broadcom 4321AG 802.11 a/b/g/draft-n Wifi Adapter in my shiny new Compaq Pressario Notebook.

A while back with an older Notebook, I used a Linuxant Driver, which I paid for, and some M$ stuff. That worked well. Now with my shiny new machine WiFI is again a problem.

Any one has a solution?

Adler

---

### Post by orb9220 on 2007-05-24
This howto is for the 4311 don't know if it works. [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=%28WifiDocs%2FDevice%29https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=%28WifiDocs%2FDevice%29https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=%28WifiDocs%2FDevice%29)

---

### Post by Adler on 2007-05-24
Orb9220,

I **did** look @ that before. I need a simpler solution. Really. 

Hasn't anyone gotten the idea that WiFi, Notebooks, and Linux don't play well together?

Adler

---

### Post by totalnub on 2007-05-24
maybe try booting with the irqpoll option?

---

### Post by orb9220 on 2007-05-24
> Hasn't anyone gotten the idea that WiFi, Notebooks, and Linux don't play well together?

Yep we know. But don't blame ubuntu and linux. Blame the closed industry that will not release drivers or even specs so the linux community could write drivers without backward engineering the damn devices.

---

### Post by Adler on 2007-05-24
totalnub,

Huh? C'mon.

Adler

---

### Post by mongooseman1128 on 2007-05-25
what's kind of funny is that if you do some sniffing around on broadcom, they're running quite a bit of Unix (open source unix)

---

### Post by Adler on 2007-05-26
theotherjoey,

How you making out?

Adler

---

### Post by Shaydog on 2007-06-23
Has anyone had any luck on this?  I've got an HP tx1000z with a Broadcom 4321AG wireless card and have had no luck thus far :(

---

### Post by Adler on 2007-06-24
Shaydog,

The way that I solved this was to buy a MYessentials 802.11g-54Mbps USB wirless device. Funny thing is that the reception strength and number of WiFi signals that I now get is better than when I ran the native device under Vi$ta. Go Linux Go! Oh, that cost me US$40.00.

If you have a PCMCIA slot -- my new notebook does not --  buy the cheapest PCMCIA Wifi card that you can find that supports WiFi G. That should get you going.

I'm not going to try playing any longer with NDISWrapper at this point.

Good Luck!

Adler

---

### Post by Shaydog on 2007-06-25
Hi Adler,

Thanks for your messages on this thread thus far.  After spending a good amount of money buying a new laptop, I wanted to try to avoid getting a new wireless card :(.  It's a shame that this is such a hassle.

I may have to go back to Windows until the Linux drivers come out for this or until ndiswrapper can support Vista drivers...

---

### Post by Adler on 2007-06-25
Shaydog,

You could also dual boot Ubuntu, and M$, then try the cheap devices that I suggested.

Adler

---

### Post by Shaydog on 2007-06-25
Adler, I actually gave it some thought and will go looking for a PCMCIA card now.  Unfortunately I'm still new to Linux and Ubuntu... when I get it, will it be as simple as plugging it in and going, or will I need to configure it with ndiswrapper?

Thanks again!

---

### Post by Adler on 2007-06-25
Shaydog,

It will that simple -- plug it it, and then select your WiFi connection with something like "Network Manager".

Buy your device at one of the larger electronics stores so that you can take it back, if it does not work. Buy the b/g card, and forget about pre-N for the time being. Let us know how you make out. WiFi is a real deal killer with Linux distros.

Adler

---

### Post by Shaydog on 2007-06-30
Well, it turns out that I don't actually have a PCMCIA slot... rather a PCMCIA 2 slot, for which the cards are significantly more expensive.  I don't think I can justify going out and getting one of those for the laptop...

Any word on when ndis-wrapper will support Vista drivers?

---

### Post by Adler on 2007-06-30
> Well, it turns out that I don't actually have a PCMCIA slot... rather a PCMCIA 2 slot, for which the cards are significantly more expensive. I don't think I can justify going out and getting one of those for the laptop...

Shaydog,

You gotta have USB ports. Go for a USB Wifi device. That's what I did.

> Any word on when ndis-wrapper will support Vista drivers?

People seem to have been able to get their internal card going, but they are better men than I! LOL!

For years now, I've not been able to get ndiswrapper to do its magic. One thing, my USB device offers faster download times, and finds more WiFi systems than when I was running Vi$ta. Go Linux Go!

Adler

---

### Post by theotherjoey on 2007-07-03
Actually, I needed to use my wireless for school, so I put this on hold. Just got back to a wired line tonight.

Once I have the $$$ I may just give in and get another card too...blah.

---

### Post by Adler on 2007-07-03
> Once I have the $$$ I may just give in and get another card too...blah.

theotherjoey,

On one hand I hear what you are saying, but on the other hand Linux is worth it! The solutions above aren't that expensive. Versus what you pay for M$, they are pretty cheap. The Community here comes free!

Don't give up, or loose your enthusiasm!

Adler

---

### Post by arron on 2007-07-03
Read this thread:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

It was made for the 4318, but im pretty sure many other models work with it.  The script is there to download, and works like a charm for me.  Worth scanning threw it all.

*edit - this driver worked best for me.  When i used the other options my speed lacked big time.

---

### Post by theotherjoey on 2007-08-01
Yes, I tried that already.

---

### Post by theotherjoey on 2007-08-01
I haven´t given up on Linux, just on this particular Broadcom card. I´m now trying to get it to work with a Linksys WUSB54GC dongle, which was supposed to work ¨out of the box¨ but instead stalls with the progress bar at 28% when i try to connect to my home network. At least my SSID is showing up though!

---

