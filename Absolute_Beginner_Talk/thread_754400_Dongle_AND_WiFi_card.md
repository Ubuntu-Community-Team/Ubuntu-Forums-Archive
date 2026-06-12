---
title: "Dongle AND WiFi card?"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by PatsyPoo on 2008-04-13
Hello everyone!
Could anybody tell me if it would be ok to use a dongle even though my machine has a WiFi card already installed?
My card (Broadcom 4311) doesn't work with Ubuntu - I tried EVERYTHING (ndiswrapper, fw-cutter, ndgistk, etc, etc, etc!) - but as soon as I enable wireless (top right) the Wifi light goes off and until I disable wireless again, there's no light.
To cut a long story short, I know the problem is the card. So my next question is: could I use a dongle on my machine even though it's already got a built in wifi card?
Because of this I've had to go back to Vista but I really liked Ubuntu and want to keep at it!
Any suggestions?

---

### Post by red_Marvin on 2008-04-13
Well I think it should work, as long as you make sure the dongle works with linux.

---

### Post by oilchangeguy on 2008-04-13
what are you going to connect the dongle to? you could just get a wireless pcmcia card that works with linux.

---

### Post by PatsyPoo on 2008-04-13
I was going to connect it to my wireless router.
I'm assuming that this pcmia card would have to be physically installed inside my machine, yes? If that's the case, the dongle would be much easier if it was possible...

---

### Post by oilchangeguy on 2008-04-13
> **PatsyPoo said:**
> I was going to connect it to my wireless router.
I'm assuming that this pcmia card would have to be physically installed inside my machine, yes? If that's the case, the dongle would be much easier if it was possible...

ok, now it makes sense, that will work. but, if you're looking to go wireless, your lappy should have a slot in the side for a pc card (pcmcia) disable the onboard wireless card. and use the adapter card.

---

### Post by PatsyPoo on 2008-04-14
So I've looked into this pcmcia card (cos I'd never heard of it before!) and it sounds like it should slot into a credit card sized tray on the said of it, is that right?
Am I right in thinking that all I'd have to do is Fn+F2 to disable my wifi card and then slot this other card in instead?
Just one more thing as well: does the fact that I was able to connect to my router through the wire mean that my router is compatible with Linux? It's just that I don't want to get extra stuff to then find out it was a waste of money because the router isn't compatible...
Sorry if I seem a bit thick - and I always thought I did alright as far as basic computer stuff goes...

PS: Lappy?! I love it! Haha!

---

### Post by red_Marvin on 2008-04-14
The protocols used to communicate with the router (and the internet) are standardized, so it should work with any operative system.

---

### Post by stalkingwolf on 2008-04-14
If you have a USB plug you can also use a usb adapter.
This site might b of use
[http://linux-wless.passys.nl/]("http://linux-wless.passys.nl/")

---

### Post by kwacka on 2008-04-14
I note you're in the UK - check out the 'Linux Emporium' at [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

The last item on the list is a PCMCIA (being a pedant I'd say its a Cardbus really) card for a tenner, but they don't offer any support; however it uses a RT2500 chipset. They say "This card works 'out-of-the-box' in Ubuntu 7.04 Feisty and 7.10 Gutsy,"

See [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

BTW, I the only connection I have with these folk is some CDs I bought from them a few years back (before I left the UK).

---

### Post by PatsyPoo on 2008-04-15
Thanks kwacka!
I had already ordered one of those cards for the exact reasons you told me I might want to have a go... It should be arriving soon and I'll post the outcome here...
:biggrin:

---

### Post by aeiah on 2008-04-15
rt2500 may not work out of the box in ubuntu. it should work, but last time i checked the drivers were broken. fear not though. the serialmonkey drivers are very good and will work well once you install them, if the card doesnt work for you out-of-the-box


oh, and fn+f2 may not work in ubuntu to disable your onboard wifi. there'll be ways of disabling it though in both ubuntu and in your bios if that key combination doesnt disable it.

---

### Post by PatsyPoo on 2008-04-19
You will all be pleased to know that my WiFi card is now up and running so I don't have any need for a dongle or a pcmcia card anymore. I'm still having trouble setting up my network but at least now I know there's nothing up with the card...
Thanks for all the posts anyway!

---

