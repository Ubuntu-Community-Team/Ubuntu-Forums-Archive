---
title: "Live CD freezes on boot"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by slockton on 2007-12-12
Hi,

I have an old(ish) HP with a P4 1.8, 1 gig RAM and a 160 Gb PATA hard drive.  I recently decided to turn this into a little music server/ MythTV box.

I got a old(ish) PNY GeForce4 MX 4000 card (has s-video out) and slapped it in a PCI slot and attempted a fresh install of Ubuntu 7.10 using the bog-standard live CD.  It freezes at exactly the same point each time during the load of the live desktop - the orange block bounces around happily for a bit then it always stops a few pixels past the third checkmark on the progress bar.

I suppose the is some kind of video driver issue - but if you can't even get to a command prompt or anything how on earth am I supposed to fix it?  What options do I have?

Thanks,
Ste

---

### Post by scrooge_74 on 2007-12-12
What speed you use to burn the CD? Try to burn it close to 2X speed if possible

Also try booting the live CD in the safe mode

---

### Post by Niniel on 2007-12-12
Actually, select Test CD from the boot menu to make sure your CD was burned without errors. That's the most common problem. 
And check the integrity of your iso file by checking its MD5 checksum.

---

### Post by aysiu on 2007-12-12
Sounds as if it corrupted during download or burn. There are ways to prevent/check this:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by omegamike3 on 2007-12-12
If you burn a second disk at slower speed that gives you the same result, then give the alternative disk a try. You won't get the fancy desktop to 'test drive' but as long as you know that you do in fact want to run the install, the alternative disk will get the job done. Plus it runs a little quicker/smoother since there isn't such a fancy GUI to load.

---

### Post by slockton on 2007-12-12
Thanks for the rapid responses!

- CD has no errors according to the install CD (that part of the CD works just fine it seems)

- Tried booting with safe graphics mode - same deal

- Will try the alternative CD later on

I've heard some ugly stories about linux and graphics card drivers, could that be the problem?

Ste

---

### Post by philinux on 2007-12-12
Would it make any difference if the card was in the AGP slot

---

### Post by omegamike3 on 2007-12-12
> **philinux said:**
> Would it make any difference if the card was in the AGP slot

PCI card in an AGP slot = no worky :)

---

### Post by markyb86 on 2007-12-12
> **philinux said:**
> Would it make any difference if the card was in the AGP slot

They aren't the same size

---

### Post by philinux on 2007-12-12
Not a hardware expert I thought that card was an AGP type, and wondered how it could go in a pci slot? :)

---

### Post by slockton on 2007-12-12
Heh, no - it's a PCI card in a PCI slot. :)

Ste

---

### Post by philinux on 2007-12-12
When you boot the livecd .

Get to the initial boot up screen and then press F6 for further options. Move the cursor across and remove the words "quiet" and "splash" then press enter to boot.

You should then get the boot messages on the screen. When it hangs, make a note of the last few lines on the screen and post back.

---

### Post by slockton on 2007-12-12
> Get to the initial boot up screen and then press F6 for further options. Move the cursor across and remove the words "quiet" and "splash" then press enter to boot.

You should then get the boot messages on the screen. When it hangs, make a note of the last few lines on the screen and post back.

Hi - did this and here are the results (this is with LiveCD, not alternate CD yet)

I took a picture of the screen as there are too many random numbers floating about to type out... what do you guys think?

[IMG]http://grad.bio.uci.edu/ecoevo/slockton/ubuntucrash.gif[/IMG]

EDIT:  btw, the computer is locked-up at this point.  The cursor is flashing but no amount of ctrl-alt-del can reboot it...

Cheers,
Ste

---

### Post by slockton on 2007-12-12
I have some further information...

I saw on the back of the HP that it had a VGA port, so probably on-board video.  I then did the following:

- Went into the BIOS and found the VGA device order and changed it from "PCI-VGA" to "Int-VGA".  
- Saved the BIOS settings
- Switched the VGA cable from my card to the internal graphics VGA port 
- Rebooted.  

It worked just fine, booting to the live desktop.

So, it does seem like some kind of graphics card issue.  I browsed this and other forums and people seem to have success with nvidia geforce4 mx 4000 cards, so what is going wrong?

One possible option is this:  When you get to the liveCD's menu you have the option of installing with "driver update CD".  Can I somehow use this option to get the liveCD to use my video card properly?  If so, how?

Thanks,
Ste

---

