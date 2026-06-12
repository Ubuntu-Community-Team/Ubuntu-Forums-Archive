---
title: "Ethernet card?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-08-19
I've been gifted with a 2nd computer and want to network it with my old one so I can use Win98 on the old, slow machine and Kubuntu on the new one. I have the router and the ethernet cables. The new machine *seemed* to have an ethernet card. This is the lspci output when I first got the box.

lspci
0000:00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. 
RTL-8139/8139C/8139C+ (rev 10)

but there was no place to put the ethernet cable. The previous owner, who knows nothing about hardware, swore he used an *ordinary telephone wire*(!?) that he plugged into the dialup modem jack on the computer and then into his router to use his DSL modem. Everyone I've spoken to about this is highly skeptical, as am I, but that's all the info I have.

I'm on dialup, so I need the dialup modem (an Intel536ep), which is working fine. 

I put an ethernet card with a real ethernet cable jack into the new computer, but neither Linux nor WinXP (also on this new computer) can detect it. They both see the original Realtek card. Below is the *total* output of lspci after installing the new ethernet card.

lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:0a.0 Communication controller: Intel Corporation 536EP Data Fax Modem
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
0000:00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

Now I'm stuck. Could the new ethernet card be bad? Or is there a way to tell Linux I've got a second one, and which to use? I'm not crazy about opening the box again and pulling anything out--especially as I don't recall seeing anything that looked like an ethernet card in there. I suspect it's wired either to the dialup modem or the motherboard. Is that possible? 

PS: Wasn't sure where to put this, hardware or networking, but I know I'm an absolute beginner at this.

---

### Post by coffeecat on 2006-08-19
Most (all?) computers made recently have ethernet controllers built in to the motherboard. They don't have separate pci ethernet cards. Are you sure there isn't an ethernet (RJ-45) port somewhere among the USB and audio sockets? It's often next to two of the USB ports. I don't understand why Linux doesn't recognise the ethernet card (was it a pci card?) you put in, unless, as you say, the card is bad. Windows won't recognise it until you install a driver for it, but it should pop up a 'found new hardware' balloon.

Whatever, you must have an ethernet controller already if lspci lists it, and lspci doesn't just list devices plugged into a pci expansion slot. It will list an ethernet controller built into the motherboard. I wonder if the previous owner thought the ethernet port was a telephone jack port. They're vaguely similar in appearance, although different in size, at least in the UK.

What is the make/model of your computer, and do you know which motherboard you have? With this information it should be easy to check what ports you have at the back and where they are.

---

### Post by editrix on 2006-08-19
Thanks for being so quick!

> **coffeecat said:**
> Most (all?) computers made recently have ethernet controllers built in to the motherboard. 

Shows you how old my old computer is :-)

> Are you sure there isn't an ethernet (RJ-45) port somewhere among the USB and audio sockets? 

As sure as I can be. All I can see are the standard 2 dialup modem jacks. They're the same size, not big enough for an ethernet plug.

> I don't understand why Linux doesn't recognise the ethernet card (was it a pci card?) you put in, 

Um, what's a pci card? It just looks like all cards look: green, with a bunch of silvery things and wires. And the ethernet jack, of course.

> Windows won't recognise it until you install a driver for it, but it should pop up a 'found new hardware' balloon.

Darn! I of course had a printer plugged into the box, using it on Linux but never installed it in Win. So I assumed when the "new hardware" notification came on, it was the printer. I'll have to get back into XP to see, now.

> I wonder if the previous owner thought the ethernet port was a telephone jack port. They're vaguely similar in appearance, although different in size, at least in the UK.


Same here in North America. Except, no, there's really only the 2 modem port, and I asked him 3 times, "Are you sure it was just a regular telephone wire you used?" I'm pretty sure he knows the difference between that and an ethernet cable.

The box sat around in a cupboard for about a year before he gave it to me, so his memory may be foggy.

> What is the make/model of your computer, and do you know which motherboard you have? With this information it should be easy to check what ports you have at the back and where they are.

The computer is one of those build-you-own Protevas. That is, you walk into a computer store, and at their computer you select the bits and pieces you want, and a couple days later you come in to pick the machine up.

The motherboard is a GA-7VKML (I think). I found a large sticker that's a diagram for one in all the bumpf he gave me. There's one box shown that's labelled USB LAN. But I can't tell if that means USB and/or LAN or it's a USB-type of LAN, if such a thing exists.

---

### Post by coffeecat on 2006-08-19
> **editrix said:**
> All I can see are the standard 2 dialup modem jacks. They're the same size, not big enough for an ethernet plug.

No - I should think these are attached to a pci card (see below). Look higher up - see my last comment.

> **editrix said:**
> Um, what's a pci card? It just looks like all cards look: green, with a bunch of silvery things and wires.

Yes, that's right - green and silvery. :) If I've identified your m'board correctly (see below), there are three white sockets on the board for pci cards. The brown one is an AGP socket for a graphics card.

> **editrix said:**
> The motherboard is a GA-7VKML (I think). I found a large sticker that's a diagram for one in all the bumpf he gave me. There's one box shown that's labelled USB LAN. But I can't tell if that means USB and/or LAN or it's a USB-type of LAN, if such a thing exists.

USB LAN would be something else. A google search came up with [this](http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=1306). Remember, google is your friend. :wink: If this is indeed your m'board, then you definitely have an ethernet RJ-45 on the rear panel:

> Rear Panel I/O[LIST=1]
[*]2 x USB1.1 ports
[*]1 x COM port
[*]1 x RJ45 LAN port
[*]1 x LPT
[*]PS/2 Keyboard, PS/2 Mouse and
[*]1 x VGA port[/LIST]If you click on the picture of the board in the link I've given you, you'll get an enlarged view. See if this is the same as what you've got. Also, on that page is a link to download the manual. The English language PDF version of this is just short of 5 Mb. I know you're on dial-up, but it might be worth downloading. I'll tell you for free that on page 16 it shows the back panel and there's the ethernet port next to 2 USB ports, just below the keyboard and mouse PS/2 ports. Have another look. :)

---

### Post by editrix on 2006-08-19
> **coffeecat said:**
>  Remember, google is your friend. 

See my sig :-) But sometimes, you have to know what to ask. Frankly, it never occurred to me to google it this way--my head wasn't there, if you know what I mean.

> If you click on the picture of the board in the link I've given you, you'll get an enlarged view. See if this is the same as what you've got. 

Okay, now I'm out of my depth, which means I'm going to have to call in onsite help: i.e., someone who's seen the inside of a PC before. Luckily,  I know one.

He may be able to help me take it from there, but if not, please watch this space for further developments.

And thanks so much for steering me in what looks like the right direction!

> I'll tell you for free that on page 16 it shows the back panel and there's the ethernet port next to 2 USB ports, just below the keyboard and mouse PS/2 ports. Have another look.

Will have to unplug the machine to do that (the wires aren't long enough to turn it around) but I promise to, and wear my glasses while I'm doing it :-)

---

### Post by coffeecat on 2006-08-19
Afterthought. One thing I'm not clear about is how you're going to link up your Intel dial-up modem, your router, your old computer running Win98 and this newer one with Kubuntu. I know nothing about the dial-up modem. Is it a standalone box, because from what I found on google it seems to be a chipset for an internal modem? Is this right?

**Edit:** We posted more or less simultaneously, but I'll keep an eye on this thread. Best of luck!

---

### Post by editrix on 2006-08-20
> **coffeecat said:**
> Afterthought. One thing I'm not clear about is how you're going to link up your Intel dial-up modem, your router, your old computer running Win98 and this newer one with Kubuntu. I know nothing about the dial-up modem. Is it a standalone box, because from what I found on google it seems to be a chipset for an internal modem? Is this right?

**Edit:** We posted more or less simultaneously, but I'll keep an eye on this thread. Best of luck!

First off, you were quite right, the ethernet plug is there. I wasted a week on software solutions when a brighter light and more workspace would have let me see this plug--or, had I taken a good look at the back of the box when I first got it, although I hadn't been thinking networking then. Sometimes, you just need a different angle (literal or figurative) to approach something from, and you gave it to me, so thanks.

Yes, the modem is internal. I noticed I can't use it when the ethernet card is up, but at least I know about *sudo ifdown eth0*. (I have no intention of using Win to get on the internet. I'm not even sure I'll want to share the printer.) So far, just the joy of having the card detected has been sufficient. I still have to learn how to use this connection--i.e., set up RealVNC on the Win box, etc. That's my project for today.

My problem is I need a couple of Win apps for my work, but the information I get is mainly via email, so I need a way to transfer text between my Kubuntu box and the Win box, and the floppy disk solution is just too fiddly. I figure, once the two boxes are connected, I can get the data from one to the other somehow.

---

### Post by coffeecat on 2006-08-20
I'm glad you've found the ethernet port. But it's been an interesting journey - you've learnt a few things on the way. Now, if someone asks you what a PCI card is, you can reply, "It's a green and silvery thingy." :wink:

Best of luck with the networking project.

---

