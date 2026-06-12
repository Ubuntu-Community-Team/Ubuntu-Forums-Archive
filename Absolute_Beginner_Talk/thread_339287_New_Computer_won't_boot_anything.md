---
title: "New Computer won't boot *anything*"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by The Iron Curtain on 2007-01-15
Hi,
I recently built a computer and I installed Edgy Eft AMD64 on it. I kept the computer on for days, shut it down, moved it a around, turned it on, etc... Basically, it was working fine.

Now i moved it into my room and It won't boot from the HDD or from the CD.](*,) The only thing I did before plugging it all back in, is I removed the external fan speed controller and plugged the fan drirectly into the Motherboard.  (I did this because I had not need for that extra part and it was cluttering up the box).

I checked the BIOS and everything seems okay (it found everything). When I turn it on, after the POST screens and the GRUB screen it says:

```
Starting up ...
.
Decompressing Linux...done.
Booting the kernel.
_

```
(The last line is the flashing cursor)

After a few minutes, nothing happens. I turn off the PSU (because the front button won't respond) and then retry.

So, I put in the Ubuntu LiveCD (the same one I installed Ubuntu from) and it seems to read the CD (i.e. it shows the main menu) and I tell it to run Ubuntu. It runs the same screen as above. And the same results.

So, I stick in a Knoppix CD (I tested it before, so I know this CD works) and  it shows the main menu. I tell it to run Knoppix and Tux appears with information on what's happening. The screen stops at looking for USB devices. Again, no response after that.

After that, I let it rest overnight (who knows, ghosts might have been in it ;) ) much to my dismay, nothing changed.

Today, I tried booting Ubuntu, kernel 2.6.17-10-generic (recovery mode) from the GRUB menu. The screen rolls by and stops at this (I can type out the whole thing if it's needed, but it's quite long, so this is the last line):
```

[  92.233213]  io schedular cfq registered (default)

```

After that, nothing happens.

I unplugged and replugged the IDE cable and tried again.

This happened when I was first installing Ubuntu. Finally, I put in the liveCD and left for about an hour and came back and it was running.

That's all I've got.

Thank you in advance!

---

### Post by logos34 on 2007-01-15
hey there again Iron Curtain,

So is this the same mobo you had eyes on, or another?

Try booting from the livecd again, hit F6 at the menu and add this to the Boot Options line:
> elevator=as

Does that do anything?

---

### Post by The Iron Curtain on 2007-01-15
Alas, logos, it is the same mobo I was mentioning earlier. I hope it;s not a mobo problem...
Okay, I did what you told me...it now says:
```
.
Decompressing Linux...done.
Booting the kernel.
_
```

...And I'm waiting...I'll let you know when something happens...

---

### Post by The Iron Curtain on 2007-01-15
...And Nothing happened. It's still stuck at that same screen.

Any Ideas where the problem might be?

---

### Post by Ocxic on 2007-01-15
go into your bios (iether del or f2/f10, one of them) and reset everything to optimized defaults, or just default if that not there. try serching out the "ISA enable bit" or simmilar option prolly with your chipset settings and disabling it.

---

### Post by The Iron Curtain on 2007-01-15
Okay, I reset the defaults.. couldn't find anything labled ISA

restarted...same as before...

I changed the boot order to read the CD/DVD drive first and ran the LiveCD with the boot option logos said to do...still nothing new.

The icing on the cake is that if I return this mobo to newegg, they will force me to return a perfectly good AMD processor and a perfectly good Kingston RAM module with it (it came in a bundle) AND, I will have to pay them $20 to restock the two good pieces and chunk the bad part before they send me a new board...](*,)

---

### Post by logos34 on 2007-01-15
Here's what I was thinking might be the problem:
[http://linux.inet.hr/cfq_to_become_the_default_i_o_scheduler.html]("http://linux.inet.hr/cfq_to_become_the_default_i_o_scheduler.html")

---

### Post by logos34 on 2007-01-15
What about the option

> pci=noacpi 

or 
> acpi=off

---

### Post by The Iron Curtain on 2007-01-15
Okay, I did both of them and I get the same thing.

I also read that article you posted. Does this mean that I  have to use an earlier version of the kernel?

Thank you for all your help!

---

### Post by irish_flu on 2007-01-15
Try undoing the change you made (removing the fan controller) and see if everything goes back to normal; that will tell you if your change caused the problem (though I can't see how that change could have made this happen).

---

### Post by The Iron Curtain on 2007-01-16
I put back the fan controller a while back and it didn't change anything. :(

I don't see any wires loose...

---

### Post by Fitzy_oz on 2007-01-16
> **The Iron Curtain said:**
> I put back the fan controller a while back and it didn't change anything. :(

I don't see any wires loose...

Does the PC have an sd/xd/flash card reader built into the case?  My work computer does and it hangs for ages trying to detect these drives.  Maybe try disabling some of the on-board features such as the iee1394 ports and the card reader - And if you can get away with it... the usb ports.

---

### Post by The Iron Curtain on 2007-01-16
> **Fitzy_oz said:**
> Does the PC have an sd/xd/flash card reader built into the case?  My work computer does and it hangs for ages trying to detect these drives.  Maybe try disabling some of the on-board features such as the iee1394 ports and the card reader - And if you can get away with it... the usb ports.

You are my personal Jesus Christ!! It workked! I had a card reader built into the floppy drive...I plug it into the mobo...but I guess it fell out when I first booted it up... No I remember! When I was removing the fan controller, I noticed the cable fell off and I reconnected it...since then I've been having all of this trouble...

Thank you so much for that help! I think the best thing about moving to Ubuntu is the forums to help newbies like me.

Thank you all.

---

### Post by Fitzy_oz on 2007-01-16
> **The Iron Curtain said:**
> You are my personal Jesus Christ!! It workked! I had a card reader built into the floppy drive...I plug it into the mobo...but I guess it fell out when I first booted it up... No I remember! When I was removing the fan controller, I noticed the cable fell off and I reconnected it...since then I've been having all of this trouble...

Thank you so much for that help! I think the best thing about moving to Ubuntu is the forums to help newbies like me.

Thank you all.

You are most welcome :) enjoy the OS

---

### Post by ubdai on 2007-01-16
This could be the problem I've been having. The pc boots up and then just hangs.

Could well be the external usb hub and card reader that was attached. I will try tonite and see. Mine was intermittent though, sometime it booted other time sit didn't.


ubdai

---

### Post by amatten on 2007-01-16
This is something I run into a lot.  I have one client with a HPLJ printer attatched via USB to a HP workstation.  If they shut down the PC, it won't boot again until you turn off the printer or unplug the USB cable.  Kinda funny, both being HP products.

Glad you got it fixed.

---

### Post by The Iron Curtain on 2007-01-17
Yeah, I'm glad it works..but now I don't have a card reader...oh well, it's integrated with the floppy drive, so it's not taking up any space...but still

I wonder if there are any work-arounds to getting the card reader to work.

---

### Post by Fitzy_oz on 2007-01-17
> **The Iron Curtain said:**
> Yeah, I'm glad it works..but now I don't have a card reader...oh well, it's integrated with the floppy drive, so it's not taking up any space...but still

I wonder if there are any work-arounds to getting the card reader to work.

Can you isolate which part of the reader is giving you the problem - Specifically - the device type? Be it USB, SD, XD or Flash or possibly the 1394 port?  From memory they each have a cable(s) that run from the port(s) to the mb....  Try isolating each one and find out which ones work and which ones don't.  Also i found that if i plugged the reader into the board with even one pin out of whack it wouldn't boot as it would be trying to mount a drive that can't tell  whether it has media in it or not. (Particularly the card reader part).

Also can you post your mother board spec (Brand - Model - ETC)
Hope that helps....

---

