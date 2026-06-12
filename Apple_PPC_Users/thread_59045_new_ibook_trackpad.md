---
title: "new ibook trackpad"
date: 2005-08-22
forum: Apple PPC Users
---

### Post by tow21 on 2005-08-22
Took delivery of a new ibook today, and have been trying to install ubuntu (Hoary) on it.

All went according to plan so far, except - the trackpad doesn't work. Now apparently the trackpads on recent powerbooks cause difficult; and the trackpad hardware has been updated on the latest generation of ibooks, so maybe the new ibooks are using the problematic trackpads?

Anyway - I went and downloaded the appletouch driver which apparently works for the new powerbooks, in the hope that it would fix my problem.

Firstly; it won't compile against the default Hoary kernel of 2.6.10; so I opened my sources.list to point at universe packages, and installed 2.6.11. Driver then compiles successfully, insmods without complaint - but still no joy with the trackpad.

Putting the driver in debug mode shows that no events are being generated, and doing a "cat /dev/input/mice" shows nothing happening.

So: any ideas? 

(I should point out that the trackpad did work under Mac OS X, so it shouldn't be a hardware problem)

---

### Post by DJ_Max on 2005-08-22
The problem isn't with the trackpad. It's with Linux drivers. Seeing as Apple trackpad notebooks are fairly new, support for them isn't good. Do a search on these forums. Also, you can take a look here. [http://ubuntuppc.info/index.php?node=64](http://ubuntuppc.info/index.php?node=64)

---

### Post by tow21 on 2005-08-22
Did you actually even bother reading my post at all?

I specifically said I'd downloaded and compiled the driver referred to in that link; I went into detail about precisely which version of ubuntu I was using, and which kernel I was compiling against. I mentioned exactly which diagnostics I'd run to see whether the driver was picking up trackpad events.

Anyone else have anything helpful to say?

---

### Post by SirKalten on 2005-08-23
it works clean for me, but I can't right click so thats a bit annoying.

---

### Post by tow21 on 2005-08-23
[QUOTE=SirKalten]it works clean for me, but I can't right click so thats a bit annoying.[/QUOTE]

Thanks - but do you mean that

a) the trackpad worked fine for you with the default Hoary install

or

b) it didn't work with the default Hoary install, but you downloaded & compiled the driver, and then it worked ok.

If you mean a), did you have to do anything else to get it to work, or did it work by default.

And if you mean b), against which kernel did you compile it?

(And can you just confirm that we are both talking about the new model iBooks; produced after 26th July 2005, which have a new trackpad.)

---

### Post by DJ_Max on 2005-08-23
[QUOTE=tow21]Did you actually even bother reading my post at all?
[/QUOTE]
No, I usually try to help people without reading their post, it's a new hobby. What a stupid question to ask.  :roll: 

> and the trackpad hardware has been updated on the latest generation of ibooks, so maybe the new ibooks are using the problematic trackpads? 
As I said in my first reply, there's nothing problematic about the new trackpad hardware that I know of. If you take the initiativedo some reading, you will probably find your answer.

---

### Post by tow21 on 2005-08-23
[QUOTE=DJ_Max]No, I usually try to help people without reading their post, it's a new hobby. What a stupid question to ask.  :roll: 

As I said in my first reply, there's nothing problematic about the new trackpad hardware that I know of. If you take the initiative to do some reading, you will probably find your answer.[/QUOTE]

Because obviously there's no chance I might have actually done some reading before asking a question. There's no chance at all I might have actually spent several hours looking for information before coming to ask a question, in order to avoid wasting people's time. What a stupid suggestion. :roll:

1) That's actually precisely the opposite of what you said earlier, where you suggested that due to the trackpad hardware being new, there were in fact problems. Despite the fact that you then pointed me at a page referring only to PowerBooks, not iBooks.

2) The new (post-26th-July) iBooks have been widely reported to have new trackpad hardware. It's not unreasonable to think that maybe it's related to the current Powerbook trackpad hardware.

3) However, having searched fairly extensively both here & elsewhere, I can't find reports of anyone who has tried installing any variety of Linux at all on new-model iBooks. (if you can find a reference, I'd appreciate it)
This is not entirely surprising since they've only been out for about 3 weeks. Nevertheless, I thought it possible that someone had tried it, and this seemed a reasonable place to ask.

4) Since it didn't work for me, plausible reasons are
  a) There's no change in hardware & I'm doing something stupid. Always possible. Would be glad to be corrected.
  b) The trackpad is completely new hardware & no driver exists yet. 
  c) The trackpad is related but not identical to the powerbook trackpad, and the appletouch driver will work with a little tweaking for USB ids and the like.
  d) The trackpad has changed, the appletouch driver works, and I've done something wrong in compiling or installing it.

I was hoping I'd get responses that helped narrow down my options.

---

### Post by coalquay404 on 2005-08-25
[QUOTE=tow21]Did you actually even bother reading my post at all?

I specifically said I'd downloaded and compiled the driver referred to in that link; I went into detail about precisely which version of ubuntu I was using, and which kernel I was compiling against. I mentioned exactly which diagnostics I'd run to see whether the driver was picking up trackpad events.

Anyone else have anything helpful to say?[/QUOTE]

You're a pissy little prick, aren't you? You should learn some manners.

---

### Post by gruepig on 2005-08-25
[QUOTE=tow21]
All went according to plan so far, except - the trackpad doesn't work. Now apparently the trackpads on recent powerbooks cause difficult; and the trackpad hardware has been updated on the latest generation of ibooks, so maybe the new ibooks are using the problematic trackpads?
[/QUOTE]

Sorry, I don't think I have anything very helpful to offer, but I have been wondering this as well (considering buying a new ibook) and would very much like to know the answer.

For what it's worth, I've found Yellow Dog to be very good about listing what hardware they can and can't support.  For the new PowerBooks, they say they are still working on trackpad support and in the mean time are shipping complimentary mice.  They have no such note for the new iBooks, and only mention that AirPort Extreme and Bluetooth Built In are unsupported.  This implies to me that either it can be made to work without too much fuss, or they've written their own driver, or they haven't updated their website (less likely option).  So that's encouraging.

But it does sound like you've tried everything that I would have tried and that it's somewhat likely it just doesn't work at the moment.  :(

---

### Post by tow21 on 2005-08-26
[QUOTE=gruepig]Sorry, I don't think I have anything very helpful to offer, but I have been wondering this as well (considering buying a new ibook) and would very much like to know the answer.[/QUOTE]

From the Debian-PPC mailing list, I've just noticed this:

[http://lists.debian.org/debian-powerpc/2005/08/msg00342.html](http://lists.debian.org/debian-powerpc/2005/08/msg00342.html)

A short patch is necessary for the appletouch driver, to add the USB id of the new trackpad.

Haven't had a chance to try this out and I won't have time until some time over the weekend, but I hope it's useful for someone.

---

### Post by stwog on 2005-09-30
I just bought a new Powerbook and I need a small Linux partition to do some programming asignments for school. Its not that big a deal that I wont have the airport working, but the trackpad is a must.

How do I go about applying this patch? Any help?

Simon

---

### Post by prometoys on 2005-10-16
hi,

i built a kernel for the new ibooks based on kernel 2.6.14-rc4 (not released yet) and the config from ubuntu

[http://www.prometoys.net/downloads/kernel-image-2.6.14-rc4-powerpc_0.4_powerpc.deb](http://www.prometoys.net/downloads/kernel-image-2.6.14-rc4-powerpc_0.4_powerpc.deb)

this kernel solve problems with sound, touchpad and suspend-to-ram for me

I hope an official kernel will be in breezy-backports or similar when kernel 2.6.14 is released...

---

### Post by kvidell on 2005-10-16
Has anyone gotten two-finger-scrolling to work in Ubuntu yet? (Aside from any functionality at all, apparently)
It's one of the handiest features of the new iBooks and PowerBooks when running OSX.
- Kev

---

### Post by prometoys on 2005-11-17
this could help, i read about it in the debian-powerpc mailinglist[1]

[http://www.artha.org/shammash/ppc/adb_syn/](http://www.artha.org/shammash/ppc/adb_syn/)

but this is only for adb trackpads. my trackpad is a usb device

check /proc/bus/input/devices to know your trackpad type.

regards,

keywan


[1]http://thread.gmane.org/gmane.linux.debian.ports.powerpc/32013

---

