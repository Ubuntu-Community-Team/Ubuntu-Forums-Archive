---
title: "G3 Powerbook with dead CD drive install?"
date: 2008-06-08
forum: Apple Hardware Users
---

### Post by gphaze on 2008-06-08
I have a "pismo" G3 Powerbook; 400mhz G3, 384 MB of RAM, but which has a dead CD/DVD drive, so I can't mount the Ubuntu CD on the pismo's own drive.

I tried having another of my macs being in firewire target disc mode, with the ubuntu CD in THAT mac, but I couldn't get the pismo to mount the ubuntu CD that way, either.

and my experience installing ubuntu on an external drive-- as in the case of mounting the Pismo as the fire wire target disc and installing with the ubuntu CD in another mac -- also not good; the installer didn't seem to want to do it.

So, I'm tapped for ideas, unless it would work to load the ubuntu .iso onto a USB thumb drive like a cruzer.

Before I try that, anyone know if it'd work, and if so, what the pitfalls might be?

thanks!

gphz

---

### Post by stream303 on 2008-06-08
If you have a stand-alone external firewire cd/dvdrom drive, you can install with that by going into openfirmware and using this command:

```
boot fw/node/sbp-2/disk:,\install\yaboot
```

(no space after the comma, and be sure to type *boot* at the OF boot prompt when you boot by holding down CMD-Option-O-F)

---

### Post by gphaze on 2008-06-08
OK..thank you for that.

I take it this won't work if I try to use a Mac Mini as the "player?" if I put a Mac Mini (which has a super drive) in target disk mode, load the ubuntu .iso disk into that, and try to mount it from the pismo?

why couldn't that disk drive have puked AFTER I installed ubuntu!  ;-)

gphz

---

### Post by stream303 on 2008-06-09
Just to be sure that the drive isn't really dead - did you burn at a very slow speed, such as 2x or 4x, as an iso image not just copied over, and onto CD-R and NOT CD-RW?

Or is it truly gone?

---

### Post by gphaze on 2008-06-09
Yeah, I burned an iso disc at the slowest speed offered by my burner (8x).

I'm pretty sure the drive is dead (or in need of cleaning) bcs *no* disc of any kind will mount on it.

be nice if it would be possible to "trick" it into regarding another mac's superdrive as an external drive, but I guess what's fighting that are the drives' various ID numbers?

gphze

---

### Post by stream303 on 2008-06-09
How about a netboot from your other machine?  I don't think I've ever heard anyone here try it, since most resort to using external cdroms if the internal is dead.  It would be interesting to see if this might work on PPC:

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

I haven't done it myself, so I can't say for sure.

---

### Post by gphaze on 2008-06-09
that looks promising...I need to try when I have a few moments.

I'm certainly in no mood to try to buy a replacement DVD player for a 10-year old and discontinued powerbook!

thanks!

gphz

---

