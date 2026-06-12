---
title: "iMac 9.something... is it worth saving?"
date: 2006-09-19
forum: Apple PPC Users
---

### Post by ricardisimo on 2006-09-19
I promised my father-in-law that I'd check out his iMac, which is not working properly, and see if Ubuntu could save it. I'm assuming that I dowloaded and burned the correct ISO image, so we'll leave that for now. When I turn on his com, I get the chime, then a grey screen with a folder in the middle that flashes a question mark and that Apple "face", alternating between the two. That's it. I know nothing about Macs myself, but I'm assuming this means that it can't find whatever files and folders it needs to boot up properly. I'd appreciate any suggestions, including whether or not this is now a paperweight or a doorstop. TIA.

---

### Post by linear on 2006-09-19
If you are trying to recover files, you'd have an easier time booting from a Mac install disk.

If that's not available, try booting with the Ubuntu Desktop CD. Be warned that if this is an iMac G3, you'll need to do some tweaks to get video working properly.

You'll also need to explicitly mount the Mac's HFS partition, assuming it isn't hosed.

Directions for the above can be found in this forum.

(If you don't care about the stuff on the iMac disk, just run the installer.)

---

### Post by 3rdalbum on 2006-09-20
Does this just happen when you put the Ubuntu CD in, or does it happen when you're booting off the hard disk?

Mac OS 9 suffers the same kinds of corruption problems as Windows. With OS 9, there's what I call the "Error -103 of Death"... when you start getting this error, it means that your hard disk is about to crash. If you get the flashing icons when you start up from the hard disk, this means that the system software or directory structure on the disk has crashed.

His computer might not have enough RAM to run Ubuntu, if it's not been upgraded. Some of the G3 iMacs actually came with 32 megs. Unfortunately, as far as I know, you can't upgrade them to 128 megs (enough to run Breezy, albeit very slowly) without removing the CPU. This means a trip to the Apple store.

If you've got a Breezy Live CD from ShipIt, use that. Some iMacs have trouble booting the Dapper Desktop CD, and a lot of them also have problems reading CD-Rs.

---

### Post by ricardisimo on 2006-09-20
> Does this just happen when you put the Ubuntu CD in, or does it happen when you're booting off the hard disk?

It happens the first and sometimes second time I turn the machine on. After that I get nothing, just a chime and no screen, which leads me to believe that there may be a hardware problem, at least a cooling problem and maybe more.

> His computer might not have enough RAM to run Ubuntu, if it's not been upgraded. Some of the G3 iMacs actually came with 32 megs. Unfortunately, as far as I know, you can't upgrade them to 128 megs (enough to run Breezy, albeit very slowly) without removing the CPU. This means a trip to the Apple store.

I'm pretty sure it's already been upgraded in basic ways like this.

> If you've got a Breezy Live CD from ShipIt, use that. Some iMacs have trouble booting the Dapper Desktop CD, and a lot of them also have problems reading CD-Rs.

Don't have it. Once the iMac is on, flashing the "?" and the face, I can put the Dapper disk in and I get a Welcome screen for Ubuntu Live CD, a couple of elipses... loading... white screen... black with a prompt... and then... 

> [ 101.885057] RAMDISK: ran out of compressed data
[ 101.885372] invalid compressed format (err...

[INDENT][/INDENT]Crap! there was more after the "err", and another line or two after that, but the screen just shut off. Looks to the untrained eye quite a bit like overheating, but what do I know? One last thing: pressing "c" on startup does nothing. The same screen either appears or doesn't, just like if I press nothing. I've also tried the Command key, as well as Control in combination with all sorts of keys... nada. My car keys had some effect, but I had to throw them very hard right at the screen.
[INDENT][/INDENT]OK guys. Sock it to me. Personally, I'd like nothing more than to tell him he has a paperweight and send him across the street for a $250 PC. On the other hand, I can enjoy a challenge, assuming that there is even the remotest possibility of fixing this. Is there? TIA.

---

### Post by zxee on 2006-09-21
I've fooled around with macs and imacs. The 2nd generation imacs actually run pretty fast IMO with breezy or OSX. Take a look at the bottom of the imac and find out what you have-all the specs are there. If it's a 400mhz (check ram too) or better you probably can get it going

---

### Post by jdp on 2006-09-21
A slot loading iMac will have the spec on the bottom.  An older tray-loader will have the specs on a sticker inside the port area on the right side.  Tray vs slot makes a big difference when diagnosing hardware trouble.  I'm guessing tha because the RAMDISK ran out of data, then it's got a small amount of RAM.  Tray loaders shipped with 32MB or more, as pointedout above.  Slot-loaders shipped with 64MB or more, and are easy to upgrade and take normal PC-100 RAM.

---

