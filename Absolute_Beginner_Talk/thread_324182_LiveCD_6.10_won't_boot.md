---
title: "LiveCD 6.10 won't boot"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by sanvig on 2006-12-23
I'd really love to have a go at Ubuntu and with time ditch Windows, but ...

Having DL'ed, checked and burned the Ubuntu 6.10 normal x86 version, it won't boot. That is: The CD won't boot, so this really isn't an install problem; I never get as far as trying to install anything :-(

The problem seems to be with the X - it stops with an error some 95 prct into the progress bar, the error screen is a garbled "ASCII graphics" screen telling me X server couldn't load. When I continue without X the boot process stops with a black screen and a cursor that doesn't seem to do anything but blink; it's not some sort of command line thingie as far as I can tell.

CTRL+ALT+DELETE will stop the system though, unload whatever has loaded and eject the CD.

Checking through the log seems to tell the GFX get's detected allright, and then boom! "No device found".

The AMD64 version of Ubuntu 6.10 stops dead in the tracks long before this.

My config is:

AMD64 3500+ CPU.

ASUS A8N-SLI Deluxe MoBo

ATI X800-XL GFX

2*300 GB S-ATA Seagate Barracuda 7200.9

1 GB DDR-400 (2*512 MB in dual channel) good quality low latency RAM.

Generic CTR monitor, mouse, keyboard etc. Nothing fancy there.

Any help would be welcome ... thx.

---

### Post by Scorpuk on 2006-12-23
If your motherboard has an onboard graphics card could you try removing the ATI card to see if you get any further?

---

### Post by sanvig on 2006-12-23
No, there's no onboard. Only the ATI which is on a PCI-E bus.

---

### Post by Scorpuk on 2006-12-23
Not sure what else to suggest, maybe try the alternative version or the server version.

---

### Post by jvc26 on 2006-12-23
The 95% bit of your post - does that refer to 95% of the LiveCD OS loaded? Are you planning to install or are you planning to just try it out for a bit with the live cd and see how it goes? As if you're planning to install to have a look at it you could try installing with the alternate install cd (without the graphical stuff) and then see if it works from then. Also, you could then boot into ubuntu, and if the graphics still arent working you could try to reconfigure X from the command line to your gfx card if that is what the problem is. (which is mentioned in several posts across this forum)

Il

---

### Post by sanvig on 2006-12-23
It's the LiveCD OS - the progress bar at the bottom stops around 95 pct full when things go astray.

I'd just like to see the look and feel of Ubuntu before I actually devote some time to installing - I've had a bad xperience a long time ago with some ancient version of Red Hat which at the time definitely was NOT ready for mainstream consumption :-)

... but could the X thing be some sort of wild goose chase? The log lists the gfx correct as an ATI X800-XL after running through a truckload of other ATI cars/chips, as far as I can tell there's no problem with the PCI-E bus either. It's a bit weird ...

Could it be my S-ATA anly HDs causing trouble?

And is it possible to switch of X when booting from the CD?

---

### Post by jvc26 on 2006-12-23
I'm afraid I dont know the answer to that one, but there are most likely to be folks on here who do - I'll leave it to them :) good luck,
Il

---

### Post by Scorpuk on 2006-12-23
SATA drives should not cause any probs at all. My box has almost an identical spec as yours, but uses an nVidia card.


Spec here: [http://scorpuk.plus.com/phpsysinfo]("http://scorpuk.plus.com/phpsysinfo")



Not sure about switching off X on the live cd...

---

### Post by RoaringOasis on 2006-12-23
I'd suggest verifying your CD. On the CD boot menu, there should be an option that allows you to do this.

I think the two most likely issues would either be a corrupt CD, or some config issue with the Gfx Card... I'm having issues with black screen at X too, though not the exact same problem you're having... and I'm running an X1300 v1.3 (AGP) on an EPOX board with an AMD64 3000+.

---

### Post by riven0 on 2006-12-23
Going out on a limb here, but when you get to 95% and the screen goes garbled can you hit CTRL + ALT + F1 and see if it takes you to console mode?

---

### Post by sindrum_murdnis on 2006-12-23
Im not able to load my live cd right now. with that said i do believe there is a safe graphics mode you can select before the disc starts the boot. I have had to use this a few times when my ati card doesn't want to work right.

---

### Post by sanvig on 2006-12-24
#9 - the CD boots perfectly on the kids (older) box. Which is an Athlon XP 2500+, ASUS A7N MoBo and an nVidia 5900XT gfx and 1 GB RAM. Which might indicate a GFX-issue, except for the Kubuntu thing mentioned below.

#10 - I'll try that.

#11 - Same result. Stops same place.

I tried to DL Kubuntu 6.10 for AMD64, and it loaded X just fine. But then stopped dead while "loading enterprise volumes" or something to that effect. As far as I can tell that's definitely a HD-issue - is there any difference between Kubuntu and Ubuntu other than Gnome/KDE?

Guess Ubuntu won't be coming home for Christmas.

Thx for helping out so far and merry Christmas/Happy Holidays ... :-)

---

### Post by spockrock on 2006-12-24
ok, pop in the live linux disc, then press F6 I believe and use the noapci option to boot, and that will fix it (in theory), but you will have to install your gfx driver in single user mode if it does the same after install.  Or you can install from the alternate disc.

---

### Post by sanvig on 2006-12-25
*Sigh*

Installed from the Alternate CD, but at reboot there's no prompt to choose from OS' ... just merrily boots Windows up?

Answered "Yes" when asked if I wanted to install GRUB. Everything seems to be running along just fine, yet still close but no cigar ... :-(

---

### Post by spockrock on 2006-12-25
> **sanvig said:**
> *Sigh*

Installed from the Alternate CD, but at reboot there's no prompt to choose from OS' ... just merrily boots Windows up?

Answered "Yes" when asked if I wanted to install GRUB. Everything seems to be running along just fine, yet still close but no cigar ... :-(

ok two things.....why this happens that I have experienced or have helped people troubleshoot.  First installing from the alternate disc means that grub is installed on hd0.  Now if you have an IDE drive or a mix of both ide and sata, then hd0, is the master drive your IDE0 channel.  If you have only sata drives then its on your SATA0 channel.  You have to look at your post and bios information, and it will tell you which drive is connected to what channel.  That being said, in your boot menu, it may ask you a specific drive you want to boot off.  When I first install ubuntu what was happening is I had my boot option set to my windows sata drive, once I changed it to my ide drive, grub showed up and I could boot into windows and ubuntu properly.

Another thing I have seen fail on some people machines, is when they partition and install they don't set, the "/" partition with the bootable flag.  I know its really weird, but after that I have seen grub show up, and then people are able to boot into ubuntu.

So if your board is like mine make sure you double check which hard drive you are booting from, or set your "/" partition to be bootable.  I hope that helps you out.

---

### Post by sanvig on 2006-12-26
Well - I de-plugged the other drive with a clean "rescue" Win XP installation, booted and voila! Re-plugged drive no 2 and things are still fine.

Don't ask me why :-)

Now I'm stuck with the X-server problem. I'll go search for a fix for that - tried reconfiguring and taking the safe bet all along, but it's still broke.

---

### Post by spockrock on 2006-12-26
ok if you have a newish video card plx install the ati fglrx drivers.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-02330ccb580b6a9411d32bf617cc5a82116ba6b9](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-02330ccb580b6a9411d32bf617cc5a82116ba6b9)

---

### Post by sanvig on 2006-12-26
Bingo ... !

Thx a lot for helping out.

---

### Post by spockrock on 2006-12-26
hey no problem

---

