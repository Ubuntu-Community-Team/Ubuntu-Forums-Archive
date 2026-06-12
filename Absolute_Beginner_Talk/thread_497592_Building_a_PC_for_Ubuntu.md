---
title: "Building a PC for Ubuntu"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Scipio_Publius on 2007-07-10
Not sure if this is the right place to post this but seemed as good as any.  I have a pc that is about ready to be replaced (maybe in a couple of months or so...winter project).  So I have been looking at components to build another one.  I am wondering how to approach the graphics card with ubuntu...which one has better support for Linux?

---

### Post by Old Pink on 2007-07-10
Pretty much anything Nvidia, as far as I understand, especially in Feisty. :)

---

### Post by tgm4883 on 2007-07-10
nvidia

---

### Post by Boobek on 2007-07-10
Intel... 
I have it:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
06:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
06:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

And it's fully work alter  with JUST ONE command : sudo apt-get install 915resulution :P
(because it is a notebook)

---

### Post by Skidpad on 2007-07-10
^^^^ Ok, now that we see what's under the hood, tell us exactly what laptop it is.  :)

---

### Post by tgm4883 on 2007-07-10
He said he wanted to build one.  Does intel make Graphics cards?

:EDIT:

I would guess it is either one of the Ubuntu Dells, or a System 76

---

### Post by Scipio_Publius on 2007-07-10
OK, so so far my rough draft of the PC is this

case = thermaltake LANbox
mb = asus amd socket am2 micro atx
processor = amd athelon 64 x2 4800+
gpu = geforce 8600 gts (still pondering this one since I might want something for TV but I have not made up my mind.)
harddrive = raptor 150 gb

any suggestions so far?

---

### Post by tgm4883 on 2007-07-10
> **Scipio_Publius said:**
> OK, so so far my rough draft of the PC is this

case = thermaltake LANbox
mb = asus amd socket am2 micro atx
processor = amd athelon 64 x2 4800+
gpu = geforce 8600 gts (still pondering this one since I might want something for TV but I have not made up my mind.)
harddrive = raptor 150 gb

any suggestions so far?

TV in or TV out?

I would get a core 2 duo.

---

### Post by zabien1970 on 2007-07-10
You should post what you will be using this computer for ie. gaming, editing photos/videos, business, etc.

---

### Post by Scipio_Publius on 2007-07-10
> **zabien1970 said:**
> You should post what you will be using this computer for ie. gaming, editing photos/videos, business, etc.

Good point.

This will be my personal PC so web browsing, office stuff, gaming, music, editing photos (I have never edited a video)...basically entertainment (which will include my other hobby/profession - information security).  I have also been playing with vista media addition and I like to record tv shows on it (not many...basically just Heroes and Star Trek) and figured I might try to do that on a Ubuntu box (is this possible?)

---

### Post by Scipio_Publius on 2007-07-10
> **tgm4883 said:**
> TV in or TV out?

I would get a core 2 duo.

1.  recording tv.

2.  why core 2?

---

### Post by Motoxrdude on 2007-07-10
What's your prioce range? 
I would, from experience, get a core 2 duo and would not get a raptor hdd. Sure, back in the day they where almost the fastest things around, but nowdays any sata hard drive will do.

> **Scipio_Publius said:**
> 1.  recording tv.

2.  why core 2?

Core 2 duos are a lot faster then amd's X2 and cost the same. They also run cooler and use less electricity.

---

### Post by jrandolph on 2007-07-10
I just built one and it works great for me 

but i really wish i would have went with an nvidia card because it seems that my ati card has alot of problems with beryl and things 

as for the processor - take the mans advice about the core 2 -- much better

I got an ASUS board as well 

but the only difference is that I got a 250g hard drive
and a Raidmax case

I think for what i spent my box is pretty bad a$$

---

### Post by tgm4883 on 2007-07-10
I have both an X2 and a Core 2 Duo (bought the X2 just before the Core 2 Duo was released)

The Core 2 Duo is the superior processor.

---

### Post by chipotlehero on 2007-07-10
If you are planning on using wireless, be sure to check the card you buy to this list [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
I've had to set up 2 computers that did not have linux compatible cards and it was a paaaain. Just buy one that's already compatible and it will save you alot of frustration!:)

---

### Post by rickycodie on 2007-07-10
nvidia is a superior card and is much easier to configure i have to ati's on laptops and a nvidia on my desktop, and it is a much better performer.

---

### Post by Scipio_Publius on 2007-07-10
> **chipotlehero said:**
> If you are planning on using wireless, be sure to check the card you buy to this list [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
I've had to set up 2 computers that did not have linux compatible cards and it was a paaaain. Just buy one that's already compatible and it will save you alot of frustration!:)

Good point, I have a few wireless cards laying around already but I will look into that.  Might need to get another one.

---

### Post by Scipio_Publius on 2007-07-10
> **Motoxrdude said:**
> What's your prioce range? 
I would, from experience, get a core 2 duo and would not get a raptor hdd. Sure, back in the day they where almost the fastest things around, but nowdays any sata hard drive will do.



Core 2 duos are a lot faster then amd's X2 and cost the same. They also run cooler and use less electricity.

I want to keep this below or near 1,000.  I don't need a monitor or any external accessories and I want to build it around the LANbox so micro atx motherboard is necessary.  

So far good advice fella's I will rework the config based on core2 duo and nvidia.

---

### Post by tgm4883 on 2007-07-10
> **Motoxrdude said:**
> What's your prioce range? 
Core 2 duos are a lot faster then amd's X2 and cost the same. **They also run cooler and use less electricity.**

This is so true.  When I first installed my C2D, I thought the fan was broke, as it wasn't running.  After a little investigation I found that it runs so cool that while the computer is running it almost doesn't need to do any active cooling.  Turns on for about 1 second every 5 to 10 seconds.

---

### Post by lbelloq on 2007-07-10
I was about to create a new thread about something similar, good I found this.

So, if I want to build a computer for Ubuntu, the components might be:

Processor: Intel Core 2 Duo
Motherboard:
RAM: 1-2 GB Kingston will be OK, I think.
Hard disk(s):
Video card: nVidia, 7xxx or better.
Audio card:
Network card:
Monitor/flat panel:
Keyboard:
Mouse:
Extras (Bluetooth, physics, card reader, etc):

I'm interested because I mgiht be able to buy a computer in the next months and gonna install Ubuntu for sure. USD 1500 is the theorical limit.

---

### Post by tgm4883 on 2007-07-10
> **lbelloq said:**
> I was about to create a new thread about something similar, good I found this.

So, if I want to build a computer for Ubuntu, the components might be:

Processor: Intel Core 2 Duo
Motherboard:
RAM: 1-2 GB Kingston will be OK, I think.
Hard disk(s):
Video card: nVidia, 7xxx or better.
Audio card:
Network card:
Monitor/flat panel:
Keyboard:
Mouse:
Extras (Bluetooth, physics, card reader, etc):

I'm interested because I mgiht be able to buy a computer in the next months and gonna install Ubuntu for sure. USD 1500 is the theorical limit.

Don't buy a physics card.  Also, don't forget CD/DVD Burner.  Or a case.

---

### Post by lbelloq on 2007-07-10
True, LOL.
(Why shouldn't I buy a physics card?)

Processor: Intel Core 2 Duo
Motherboard:
RAM: 1-2 GB Kingston will be OK, I think.
Hard disk(s): Two? 80 and 320 GB, SATA.
Video card: nVidia, 7xxx or better.
Audio card:
Network card:
Monitor/flat panel: 19'', widescreen.
Keyboard:
Mouse:
Extras (Bluetooth, card reader, etc):

---

### Post by wolfen69 on 2007-07-10
as far as mobos go, ive had real good luck with gigabyte boards.

---

### Post by regomodo on 2007-07-10
for the description you give most people seem to have it right. nVidia is the way along with intel stuff

A few opinions on some equipment mentioned though. I cannot see you needing a raptor or a 8600. save some money for "slower", larger and most definitely quieter hard drives.

I you can afford it go for a nice g'card, but those raptors sure are noisy.

Don't skimp out on cooling or a PSU. I use quietpc.com for my fans and psu's. I mention this as i assume (you want to record tv) the comp' will be in your living room. A silent PSU would be nice

---

### Post by tgm4883 on 2007-07-10
> **lbelloq said:**
> True, LOL.
(Why shouldn't I buy a physics card?)

Processor: Intel Core 2 Duo
Motherboard:
RAM: 1-2 GB Kingston will be OK, I think.
Hard disk(s): Two? 80 and 320 GB, SATA.
Video card: nVidia, 7xxx or better.
Audio card:
Network card:
Monitor/flat panel: 19'', widescreen.
Keyboard:
Mouse:
Extras (Bluetooth, card reader, etc):

Couple reason,

1.  Linux support?
2.  Price/performance gain
3.  Better alternative Dual Video Card setup
4.  Money better spent elsewhere.

:EDIT:

I did a little more research (admittedly my knowledge on the subject is a little dated).  After further review, I would get the physics card providing a couple things.

1.  You play games that would benefit from a physics card
2.  You get one compatible with linux

---

### Post by misfitpierce on 2007-07-10
Personally I like ATI... but they are a bit slow at grphics for linux atm... They have promised more support but have not really jumped on it at this point... So at this time Nvidia is a better option for linux b/c they support it alot better. Whenever ATI gets there stuff together i'll be plenty happy

---

### Post by stchman on 2007-07-10
> **Scipio_Publius said:**
> Not sure if this is the right place to post this but seemed as good as any.  I have a pc that is about ready to be replaced (maybe in a couple of months or so...winter project).  So I have been looking at components to build another one.  I am wondering how to approach the graphics card with ubuntu...which one has better support for Linux?

Nvida, don't get an 8xxx series as Feisty does not support it yet.

---

### Post by Scipio_Publius on 2007-07-12
> **stchman said:**
> Nvida, don't get an 8xxx series as Feisty does not support it yet.

Hummm...I was kinda hoping to get an 8800 gpu.  Which card would you recommend then?

---

### Post by Motoxrdude on 2007-07-16
Ever think about getting a laptop? My bro got this one and it works perfectly with ubuntu. Comes with a nVidia 7600 and is $800.[http://www.newegg.com/Product/Product.aspx?Item=N82E16834280004]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834280004")

---

### Post by NCAANFI on 2007-07-16
At close to $300 for an 8800gts, simply I don't think its worth and especially with the new models coming out well before the end of the year. Plus seriously there's probably a dozen dx10 games out. Probably crysis is he one I'm most looking forward to. personally i'd go with a 7900gs or an x1950pro. They pretty much will deal with every game out there comfortably.Also pointless to get a physx card the game has to support it. there's only about 10 or 20 that do. Oh and those saying C2D is more energy efficient well, let's just say independent testing by a reputable website contradicts that [http://www.tomshardware.com/2007/07/11/energy-efficiency-intel-left-out-in-the-cold/page16.html#conclusion_amd_still_offers_lowest_power_consumption_despite_l2_stepping](http://www.tomshardware.com/2007/07/11/energy-efficiency-intel-left-out-in-the-cold/page16.html#conclusion_amd_still_offers_lowest_power_consumption_despite_l2_stepping)

---

### Post by AngelBreath on 2007-07-16
Ok here you are:

CPU: What ever you prefer (Actually intel is better in dual core)
VGA: Nvidia
Modem: DSL ethernet 
Peripherals: check forums to find web camera,scanner,printer etc that surely works with ubuntu.

and you are ready...:):)

---

### Post by kiv on 2007-07-16
I've been wanting to do the same and you can get a very good ubuntu pc for a good price.. I use [www.ebuyer.com](www.ebuyer.com)

Intel Core 2 Duo E4300 1.86ghz Socket 775 FSB800 2MB Cache Retail Boxed Processor **£61.81**
Gigabyte GA-945PL-S3 Socket 775 onboard audio ATX ** £34.18**
Maxtor STM3250820AS 250GB 7200RPM SATAII 8MB Cache - OEM** £30.34**
Kingston 2GB (2x1GB Kit) DDR2 533MHz/PC2-4200 Non-ECC CL4** £39.48**
HP DVD1040i 18x DVD±RW/RAM Lightscribe Black Retail Box** £19.99**
XFX 7600GT 256MB DDR3 Dual DVI PCI-E Graphics Card** £66.54**
Raidmax Sagitta Black/Silver Gaming Case With Side Window - With 500W PSU** £49.34**
**Cart Total:  	 £301.68**

VAT: £52.79
**TOTAL: £354.74**

Monitor (if you need one) Cibox C1905 19" Widescreen TFT Monitor (1440 X 900) 5ms 800:1 Silver & Black [B]£84.99
[/B]

Intel Core 2 Duo are far superior to AMD X2 - much better performance & use less power.
nVidia have much better support in Ubuntu.

Follow others advice for wireless and such if you need it.

Hope this helps paint you  a picture of whats possible!

---

### Post by kiv on 2007-07-16
oh and post script printers are generally best... go for something like a HP.

Avoid Lexmark!

[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

---

### Post by Scipio_Publius on 2007-07-16
> **Motoxrdude said:**
> Ever think about getting a laptop? My bro got this one and it works perfectly with ubuntu. Comes with a nVidia 7600 and is $800.[http://www.newegg.com/Product/Product.aspx?Item=N82E16834280004]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834280004")

Actually I have Ubuntu running reasonably well on this Laptop.  A thinkpad t42 (wireless still sucks with Feisty and it was fine with Edgy...go figure).  My problem with laptops in general however is if they break you generally can't work on them yourself (there is a few parts you can replace but I find I have little problems with those parts).  I have a $3,000 dollar laptop sitting in my basement because the only place that has the part won't sell it to me unless they work on it and for their price I could buy the one you linked to.  No more laptops for me.  Laptops are a throw away item.  If you pay more then $500 then its money wasted.

---

### Post by tgm4883 on 2007-07-16
> **Scipio_Publius said:**
> Actually I have Ubuntu running reasonably well on this Laptop.  A thinkpad t42 (wireless still sucks with Feisty and it was fine with Edgy...go figure).  My problem with laptops in general however is if they break you generally can't work on them yourself (there is a few parts you can replace but I find I have little problems with those parts). ** I have a $3,000 dollar laptop sitting in my basement because the only place that has the part won't sell it to me unless they work on it and for their price I could buy the one you linked to**.  No more laptops for me.  Laptops are a throw away item.  If you pay more then $500 then its money wasted.

Try ebay

---

