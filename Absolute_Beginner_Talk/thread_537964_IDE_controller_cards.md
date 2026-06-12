---
title: "IDE controller cards"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by ron999 on 2007-08-29
Hi
Has anyone had experience using IDE controller cards with Ubuntu?
I have seen some second-hand ones for sale on eBay.
They have Windows driver discs with them.
When the controller is installed, with Windows, you do the 'found additional hardware' thing and then install the driver from the disc.
How will this work with Ubuntu (and other distros)?
Will Ubuntu just 'see' the card or will I have to hunt round for a Linux driver?
Any ideas?
These are examples of the cards:-[http://computers.listings.ebay.co.uk/Interface-Cards_IDE-ATA-Cards_W0QQfclZ3QQfromZR11QQsacatZ90714QQsocmdZListingItemList]("http://computers.listings.ebay.co.uk/Interface-Cards_IDE-ATA-Cards_W0QQfclZ3QQfromZR11QQsacatZ90714QQsocmdZListingItemList")

---

### Post by oilchangeguy on 2007-08-29
i've used these in a few windows computers (w/o using any driver cd) haven't tried a ubuntu computer yet. i suggest you google the card with the word ubuntu in the search line, and see what comes up.

---

### Post by ron999 on 2007-08-29
> **oilchangeguy said:**
> i've used these in a few windows computers (w/o using any driver cd) haven't tried a ubuntu computer yet. i suggest you google the card with the word ubuntu in the search line, and see what comes up.
Yes, I might try that.
So far I've downloaded several manuals from the makers' websites. There's pages and pages of info about installing drivers for all the different flavours of Windows - but when it gets to the Linux page it all goes blank. It says go to the website for more info, and there isn't any.:confused:
:lolflag:

---

### Post by oilchangeguy on 2007-08-29
> **ron999 said:**
> Yes, I might try that.
So far I've downloaded several manuals from the makers' websites. There's pages and pages of info about installing drivers for all the different flavours of Windows - but when it gets to the Linux page it all goes blank. It says go to the website for more info, and there isn't any.:confused:
:lolflag:

heres are real simple way to see if it works. if you've got one available, just install it. if not try google as previously suggested.

---

### Post by ron999 on 2007-08-29
> **oilchangeguy said:**
> heres are real simple way to see if it works. if you've got one available, just install it. .
I haven't bought one yet. I just don't want to waste my money if it's not gonna work.
:smile::cool:

---

### Post by ske1fr on 2007-08-29
Are you interested in the RAID facility often quoted as a feature of the cards, or do you simply want more parallel IDE channels for devices?  Whatever you want to do, the important part of the card is the chipset used, and whether it's supported by Linux.  I use an old motherboard, and I have additional hard drives attached by using a  Silicon Image SiI 0649 - based controller card.  These are supported in the kernel.

Check the listings carefully and do some checking to see if the chipset in the card is supported.  The Promise-based ones should be fine, or the CMD 0649-based ones - (same as mine).

If you are thinking of RAID, just bear in mind that servers from the big manufacturers didn't use cheap IDE RAID cards, they used expensive SCSI or IDE ones with onboard memory, processors and whatnot, so that the system processor wasn't heavily loaded.  The IDE cards you're looking at are designed to use the main system processor for much of the processing, so they'd have an effect on the system performance.

---

### Post by ron999 on 2007-08-29
Thanks ske1fr
I don't want to use RAID, I only want to use more IDE drives for different OS's.
I see that some of those cards specify RAID, some have it as an option.
I would choose one that has RAID as an option - and then not use the option.

When you installed your card did you need to install a driver or did Ubuntu detect it automatically?

---

### Post by Paulmd on 2007-08-29
> **ron999 said:**
> Hi
Has anyone had experience using IDE controller cards with Ubuntu?
I have seen some second-hand ones for sale on eBay.
They have Windows driver discs with them.
When the controller is installed, with Windows, you do the 'found additional hardware' thing and then install the driver from the disc.
How will this work with Ubuntu (and other distros)?
Will Ubuntu just 'see' the card or will I have to hunt round for a Linux driver?
Any ideas?
These are examples of the cards:-[http://computers.listings.ebay.co.uk/Interface-Cards_IDE-ATA-Cards_W0QQfclZ3QQfromZR11QQsacatZ90714QQsocmdZListingItemList]("http://computers.listings.ebay.co.uk/Interface-Cards_IDE-ATA-Cards_W0QQfclZ3QQfromZR11QQsacatZ90714QQsocmdZListingItemList")

The Promise cards are the most common for home users. The Maxtor card in the list is really made by Promise. 

Uncertain about Ubuntu support, but i've used the Promise cards in a dedicated disk-wiping machine, using DBAN, without incident (dban fits on a floppy). I suspect Ubuntu will just see the card.

Less certain about other brands, but they all have downloads available from the manufacturer's website.

---

### Post by ron999 on 2007-08-29
> **Paulmd said:**
> , but they all have downloads available from the manufacturer's website.
What do I have to download from their website?
There doesn't appear to be any Linux drivers there. The manuals that I've downloaded don't explain about Linux.

---

### Post by Paulmd on 2007-08-30
> **ron999 said:**
> What do I have to download from their website?
There doesn't appear to be any Linux drivers there. The manuals that I've downloaded don't explain about Linux.

Forgive the delay in response. I've found a more definite answer.

[http://hardware4linux.info/](http://hardware4linux.info/)

[http://hardware4linux.info/type/25/](http://hardware4linux.info/type/25/)

---

### Post by ron999 on 2007-08-31
> **Paulmd said:**
> Forgive the delay in response. I've found a more definite answer.

[http://hardware4linux.info/](http://hardware4linux.info/)

[http://hardware4linux.info/type/25/](http://hardware4linux.info/type/25/)

Hi
I don't think those links are any help with my enquiry.
Thanks anyway.

---

### Post by Paulmd on 2007-08-31
> **ron999 said:**
> Hi
I don't think those links are any help with my enquiry.
Thanks anyway.

If it's on the list, there is a built in linux driver. THAT should help.

---

### Post by nonewmsgs on 2007-08-31
in my experience (i have used a couple of them) PATA with the inch and a half ribbons are always OK, but SATA the ones with the two little cables and no jumpers are a pain in the *** and must be checked first.

---

### Post by ske1fr on 2007-09-01
Sorry about the delay in my response too.  

With Ubuntu the card should be detected on the first boot after installation, then the relevant "drivers" ( that's kernel module in Linux) should be "installed" without any need for manual downloads from the manufacturer's website.  Oh, you noticed they don't have any Linux drivers to download?  That's because frequently the "drivers" for Linux have been developed by "the Linux community" rather than the companies, although some may provide technical information to help that process along.  It's more like already having all the drivers for hardware available in the operating system, and just having the core operating system enable the necessary ones when new hardware is detected.  I'm not that familiar with the innermost workings of Ubuntu (can you tell :) ), for me it just works,  but that's the way I make sense of it.  If I've got it entirely wrong I suspect someone will correct me...

You want to use more IDE drives for different OS's?  You may find it helpful to get hold of some removable hard drive caddies, and install the drives in those.  The one I have has a switch that both locks the drive cartridge into the caddy, and switches the drive power on.  When the switch is on, the machine boots from that drive, when the switch is off the machine boots from another internal drive.  You don't have so much control over which devices are active, and the boot order, with add-on controller cards as you do with the motherboard controller.  A physical switch gives you that control.

paulmd's link can be used to check the cards you are interested in.   I wouldn't go for any cards that don't state the chipset used.   Have a look at the eBay seller's description and look for the manufacturer's name, such as Promise, Silicon Image, CMD, ITE.  Use the Brands link at the top of the Hardware for Linux pages to search through the list for the chipset number that's also hopefully referenced in the item description.  Bear in mind manufacturers get bought out by others, so CMD can be found as Silicon Image.

---

### Post by ron999 on 2007-09-01
Thanks for that.
It's starting to make sense to me now. About the 'drivers' being built into the Linux kernel. Same as the onboard IDE controller's 'drivers' I suppose.
Before I bid on anything I'll do as you suggest. I'll check the manufacturer or chipset against paulmd's link.
I've also found another list here:-[http://www.linux-ide.org/chipsets.html]("http://www.linux-ide.org/chipsets.html")

8-):grin:8)

---

