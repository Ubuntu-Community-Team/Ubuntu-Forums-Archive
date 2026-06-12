---
title: "Tips for buying a new MacBook wanted"
date: 2009-01-29
forum: Apple Hardware Users
---

### Post by finite9 on 2009-01-29
I'm thinking of buying a new laptop, as my current HP dv9297 is a 17" beast, too heavy to carry, too hot, and the lid hinge has a known manufacturing issue where the hinge tends to shatter (parents have same model and theirs shattered).

I'm excited about netbooks but they are too small for me!  I want 1280x800 min for a standard Gnome desktop, which means a minimum 13.3" screen, but I want crazy long battery life :)  I do not like netbooks mini keyboards, and I think the Atom/Nano will be too underpowered for me.

The specs I am looking for are:

13.3"
min 1GB RAM (do not need more)
hard disc: not bothered, min 80GB
Intel or Radeon graphics (nvidia open source driver sucks)
wifi that has full support in Ubuntu OOTB (ok if its closed driver, but prefer OSS)
gigabit LAN
DVI or HDMI output
DVD drive: not bothered
min. 5 hrs battery

Processor speed is not really an issue for me, but I prefer a mid range that will not generate too much heat and drain the battery too quickly.  I have a home server (Ubuntu of course) that has the processing power and disc space I need for media transcoding etc, and I just need a laptop for email/web, watching movies/TV shows, listening to music etc, but battery life, low heat, and LAN/wireless speeds are top priority.

I use a Thinkpad T61p 15" for work and I love it to death--best laptop i've ever used, but Lenovo only does one 13" model called X300 and it costs a fortune.  I want a high quality build, which rules out Acer and LG (too flimsy and plasticy), and both HP and Toshiba seem to weigh more and have lower battery life than Apple MacBook.  Sony costs too much for what you get.

So onto the MacBook question:

The MacBook seems to have everything I need:

13.3" 1280x800 screen
DVI out for connecting to my HDMI plasma TV
1GB RAM
Intel graphics
Wifi that seems to work OOTB (but which chipset is it Atheros or broadcom)?
Does it have gigabit LAN?  This is really a must for me.
5 hrs battery

But, how do I tell, in the shop or on a webshop, what model it is?  There seems to be like 6 or 7 different versions of the MacBook, and I'm assuming that this is seperate from MacBookPro?  Will all shops be selling the latest 5.1 MacBook now (saw on the Ubuntu wiki it was released late 2008)?

I really want to verify that there is more or less full support in Intrepid before I buy one.

Does the touchpad have two buttons or do you have to emulate right click with the touchpad?

Do I need grub2 to boot EFI or does grub 0.97 work fine?

Any tips on which specific MacBook to buy?

---

### Post by cyberdork33 on 2009-01-29
> **finite9 said:**
> and both HP and Toshiba seem to weigh more and have lower battery life than Apple MacBook.  Sony costs too much for what you get.


> **finite9 said:**
> 
So onto the MacBook question:

The MacBook seems to have everything I need:

13.3" 1280x800 screen
DVI out for connecting to my HDMI plasma TV
1GB RAM
Intel graphics
Wifi that seems to work OOTB (but which chipset is it Atheros or broadcom)?
I can't say for sure, but the newest model, I am pretty sure has Broadcom.
> **finite9 said:**
> Does it have gigabit LAN?  This is really a must for me.
Yes, according to the apple.com specs
> **finite9 said:**
> 5 hrs battery
Note here... That would be battery life using OS X... using Ubuntu cuts that almost in half. You can look through this thread:
[http://ubuntuforums.org/showthread.php?t=969183](http://ubuntuforums.org/showthread.php?t=969183)

> **finite9 said:**
> But, how do I tell, in the shop or on a webshop, what model it is?  There seems to be like 6 or 7 different versions of the MacBook, and I'm assuming that this is seperate from MacBookPro?  Will all shops be selling the latest 5.1 MacBook now (saw on the Ubuntu wiki it was released late 2008)?
Usually, there are only about two variations at the most in a store. For the most part, you can get the system with the basic specs and ask about upgrades. If you have an Official Apple Store nearby, I would strongly suggest to pay a visit and talk to some of the Mac Geniuses. They will be able to give you more details on this. (Don't expect them to know anything about running Linux on them though, and even if they do, they get the info wrong)

You can tell by price...

Pretty much everywhere should have only the latest models.

> **finite9 said:**
> I really want to verify that there is more or less full support in Intrepid before I buy one.
Here is the documentation:
[https://help.ubuntu.com/community/MacBook5-1/Intrepid](https://help.ubuntu.com/community/MacBook5-1/Intrepid)
Really I think you are better off purchasing a machine designed for Linux if you plan to only use Linux on it.

> **finite9 said:**
> Does the touchpad have two buttons or do you have to emulate right click with the touchpad?It actually has no buttons (sort of). The whole pad is one big button. The docs show how to get the various touchpad functions working though for right-click and such.

> **finite9 said:**
> Do I need grub2 to boot EFI or does grub 0.97 work fine?
Check installation instructions here:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
Basically, no you do not need grub-efi

---

### Post by finite9 on 2009-01-29
> **cyberdork33 said:**
> 
Here is the documentation:
[https://help.ubuntu.com/community/MacBook5-1/Intrepid](https://help.ubuntu.com/community/MacBook5-1/Intrepid)
Really I think you are better off purchasing a machine designed for Linux if you plan to only use Linux on it.


Thanks for the info!

I realise that it's not the easiest way to go, but getting gigabit LAN, wireless n, 13" screen and DVI/HDMI out in a laptop that has really good battery life, is quite light and has a decent solid design, is not that easy.  As I said, getting a Lenovo X300 would be ideal  if it had the spec I wanted (and costs too much).  Sony costs too much full stop.  Other brands do not have decent build quality and tend to be only usable in the home, because the shell is too flimsy.  I have not, I admit, actually felt a MacBook to test the build quality, but from images, it doesn't seem too plasticky.  I'm honestly not that bothered about the actual design...I know a lot of people buy Macs with the design being a major factor, but for me the toughness of the shell is more important.

I'll have to pop into a shop and have a look at one.

---

### Post by ryanisablond on 2009-01-29
If you go to a shop that lets you get your hands on working machines, you can look at the hardware version and all sorts of other fun spec stuff with the "System Profiler" application:

Applications > Utilities > System Profiler

Or, if you prefer, click on the Apple icon in the top left, then select "About This Mac," and click on the "More Info..." button.

My apologies if you already know this.

As for the hardness of the shell: One of the common complaints with plastic-shelled macbooks is that the exterior shell gets scuffed and scratched very, very easily. It's hard and protects the machine, but it just gets grungy looking very quickly. The black version is supposed to be better. I haven't heard anything about the new unibody aluminum models yet.

Hope this helps, good luck with the laptop hunt! :KS

---

### Post by w00t951 on 2009-01-30
If I were you, I would just save up amd then buy the new unibody MacBook Pro (Late 2008) as soon as possible, as it is WAY better then the unibody macBook and it is also much more durable uin addition to the added power from the dual graphics. if you need to connect to the HDTV, order it from the Apple webpage, and replace the Miniport with a standard mini-DVI port. It would only be a few extra dollars and the hardware is well-suited to running Mac, Windows, and any version of Linux that you need. I installed the latest version of Ubuntu on the machine and it runs extremely well, especially @ startup, when the boot sequence only takes an upwards of 6 seconds.

---

### Post by buntuLo on 2009-01-30
> **w00t951 said:**
> If I were you, I would just save up amd then buy the new unibody MacBook Pro (Late 2008) (...) I installed the latest version of Ubuntu on the machine and it runs extremely well, especially @ startup, when the boot sequence only takes an upwards of 6 seconds.

hi w00t951, it sounds great! can you tell me more about your installation, especially regarding the boot process you choosed?

i have Kubuntu 8.10 64bit running on this machine and i use rEFIt and Grub to boot it: well, just the booting stage takes more than 6 seconds in my case, then Kubuntu loads pretty fast indeed. but it still takes almost 30 seconds to have an operative desktop!

Finite9, i can confirm you that the MacBook Pro 5.1 (late 2008) looks and feel like a really good piece of hardware, and that the installation and post-installation processes are not too tricky. and i believe that also the smaller MacBook would be a good choice. enjoy choosing! Lo.

---

### Post by MikeTheC on 2009-01-30
> **finite9 said:**
> I'm thinking of buying a new laptop

I don't know how it will be for your region, but Apple is selling a revised (with no fanfare whatsoever) white MacBook with 2 GHz CPU, 2 GB of RAM, nVidia 9400M, etc. and at least here in the U.S. it's $999. You might want to check your own Apple online store (or local retailer) to ensure if this is the type of unit you're buying, that you're getting the new and not the old hardware.

Good luck!

**EDIT:** I just looked at the Apple Store/Sweden, and they show the listing I'm talking about labeled as NYHET, which I'm assuming means "New". Their price is 9495 kr.

---

