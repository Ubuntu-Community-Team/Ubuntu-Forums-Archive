---
title: "Newbie question: How about intalling drivers through Wine?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by papercuts on 2007-04-21
I have a drivers CD from my motherboard manifacturer. It works flawlessly in Windows. They have included the Linux drivers too but I can't get them to work no matter how hard I tried (It's VIA P4M890).

So how about using Wine to run the EXE setup files for drivers? It sounds very unlikely since Wine is only an emulator and doesn't probably change system settings. But it's worth asking, at least for the laughs :)

---

### Post by calraith on 2007-04-21
Yeah, you're right.  Whatever drivers you install through Wine will only be active in the context of that wine bottle.  It would do you no good.

VIA apparently publishes drivers specifically for Ubuntu on their website, for what it's worth.  [http://www.viaarena.com/default.aspx?PageID=2&OSID=45](http://www.viaarena.com/default.aspx?PageID=2&OSID=45)

---

### Post by trippinnik on 2007-04-21
Drivers installed in Wine would not work at all, they'd have no way to communicate with the hardware if there are no drivers installed in Ubuntu.  Why do you need to install the motherboard drivers? Is there something on the motherboard that isn't working?

---

### Post by Neobuntu on 2007-04-21
You have to understand what a driver is before you can understand why this is ridicules.

Basically a "driver" or "module" links a particular OS to a specific hardware model so they may communicate. Obviously it has to match the OS and it's methods. Then of course, it makes the finite device model (version, chipset etc..) "do what it do" (as the kids say).

For programs, WINE does not use the Windows OS (which is amazing). There's no performance hit. 

What I find interesting is that WINE and friends work well on so many different programs(not all), that people think the driver should just work as well. LOL While there is NO substitute for running programs in their native OS, WINE is impressive. Thing is, most people don't need it anyway. Just switch to a native open program that is without limits. WINE is good though; for special cases. *ubuntu makes it easy. You will have to fiddle a bit, but once done, it's sweet. The easy thing to do is check the progress on the Windows program you desire.

Just remember, the TERRIBLE task of rebooting for 2 minutes is the best, easiest and trouble free solution for doing both. WINE is for when you have to run it at the same time. 

Virtualizer's are for servers BTW.

Oh, and those (old) drivers you sometimes see packed on Windows install CD's are usually for compiling, which you don't have to do with Kubuntu for most hardware.  Kubuntu just makes it work and keeps it upgraded. You don't have to think about it, by in large.

You should inventory every device you have for "openness" and simply replace those poor devices. It's next to no time and very little cost. Do not fight with them. Then, never by any hardware devices before you verify it works automagically, and with zero set up time on your part. Just avoid old Windows only hardware. They can work too, but you don't want the hassle.

Put drivers on automagic!

Stay free.

P.S. On the other hand, ndiswrapper "Windows wireless drivers' kinda does this (and has a super easy GUI interface to grad your XP driver too). Use a WIRED connection to install it, then go wireless. You see, NDIS is a driver specification for windows that the network drivers use. Open software is so cool, that we have an serogate like driver module (ndiswrapper) that reads XP drivers and translates them into what Linux and the Device needs. Again, *ubuntu makes it easy. It's Just, sometimes a new trial, developing, native driver has to be blacklisted and NOT run at the same time (of course) as ndiswrapper. Again, a (working/pre-verified) native Linux driver (In *ubuntu for the device) is simpler and much better. They just work.

---

