---
title: "iMac, Xbuntu, and cds"
date: 2006-12-22
forum: Apple PPC Users
---

### Post by andy gee on 2006-12-22
More problems with cds and imacs...

I am running a (very new) project to help disadvantaged kids and senior citizens get access to technology, and in particular, the internet (and all internet experiences - eg flash). We are doing this by getting older computers for free, putting up-to-date OS on them, and handing them out for free. This also has the effect of getting Linux out to the wider community, building a grassroots, non-techie userbase, and helping to minimise damage to the environment. Xubuntu is my preferred OS - it is user friendly (for people without much computer experience) and easy enough to install.

I have just received a Rev B iMac (233 MHz, 4Gb hdd and 32 (!!)Mb RAM) and don't know what to do with it. It's running Mac OS 9.2 ok,  but I'd really like to handout something more...linux-y. And more compatible with modern technology. I've looked at Ubuntu-lite, but they don't seem to have a ppc kernel option.

I attempted to boot the ('bondi blue', very old) iMac with the PPC Xubuntu boot cd. I pressed c while booting, no luck. I got:

"This disk is unreadable by this computer.
Do you want to initialize the disk?
Name: untitled
Format: ProDos OK
               Eject Initialize"   [these last two are options]

So I put the cd in after the machine had booted up OS 9.2, and put the cd in the tray and closed it. Got the same message. Next I tried playing an audio cd. No problems. So I'm rocking out to the White Stripes, but not getting far.

The cds have been burned on a PIII pc running Ubuntu. CDs burnt on this machine are fine on other pcs. I've been using the CD/DVD burner that comes with Ubuntu, burns isos fine, and I've checked it afterwards on other pcs, and it looks good. Ubuntu x86 vers I've burned with this pc has booted other pcs fine, I've burned xbox OS with it and booted the xbox fine, so I don't think there's a problem with burning images on the pc. So, any idea how I can get this computer to read the cd?

For everyone helping me on the old thread, thanks!

---

### Post by 3rdalbum on 2006-12-23
Does the iMac sound like it's having trouble reading the CD?

Usually, they do have trouble reading burnt CDs. Try any CD that has been made "for music", including the Verbatim vinyl discs.

However, 32 megabytes is not enough to run any PowerPC Linux, except maybe a server distribution (Finnix?)

---

### Post by andy gee on 2006-12-23
Hey 3rdalbum! Thanks for your interest!

1. I tried the cd on another newer (charcoal crt) iMac and it worked ok. So the older iMac might have a problem with my cheap and crappy cds, eh? (Damn you, TDK!!) I'll try another better quality cd and see how I go. 

2. I had a feeling that Xubuntu might be too much for 32Mb. My original idea was to use Ubuntu-lite but they don't have that variant in ppc and a poster in another thread though Ubuntu would run ok.

Maybe a server install of Xubuntu? I could keep it a minimum install maybe? I'd like to stay with Ubuntu on all the machines we give away to make it easier to provide help if something goes wrong.

Anyone put linux on one of these old ppcs? or on any 32 Mb ppc?

---

### Post by Portable_Jim on 2007-01-03
> **andy gee said:**
> 
Anyone put linux on one of these old ppcs? or on any 32 Mb ppc?

No, But I want to.

What is the system requirements for fluxbox and iceWM?

---

### Post by terryeden on 2007-01-03
> **andy gee said:**
> Anyone put linux on one of these old ppcs? or on any 32 Mb ppc?

Yup - got Xubuntu running on the Rev C (266MHz) but with 158MB of RAM.

What you may need to do is update the open firmware so it will boot from the CD.  I did this a looooooooooong time ago so I'm afraid I can't remember how....

---

### Post by 3rdalbum on 2007-01-04
32 megs of RAM is not enough to run any PowerPC Linux except Finnix (or possibly text-mode Debian). Neither of these are suitable for what you're proposing, unfortunately.

It might be possible to cut down Debian to run a desktop within 32 megabytes, because that's what Damn Small Linux (for x86) does. But you'd need some skills!

---

### Post by andy gee on 2007-01-19
Well got the cds working - turns out it was a cd problem after all! Changed brands a few times and finally got there. But I'm still up against the RAM limit. Why does OS 9.2 work so well in 32 Mb RAM when Linux won't? *sigh*

I finally got a non graphical (text only) debian working, only that's not what I'm after.

Anyone got any spare RAM? ;) 

Thanks for your help guys.

---

### Post by 3rdalbum on 2007-01-19
I've just found out that one of the main reasons why DSL and DeLi can run in such a low amount of memory on x86 is because they use tiny X servers. Unfortunately, those tiny X servers are not available for PowerPC.

---

### Post by gurnemanz on 2007-01-19
> **andy gee said:**
> 

Anyone got any spare RAM? ;) 

Thanks for your help guys.

Andy, there *have* to be some other early iMacs laying around unused in Oz. They'll turn up, and you can pilfer RAM from them.

I'd send you my spares, but they're for the later 500 mhz Indigo and Ruby models, and use a different RAM module configuration.

It's a great project you have going - best wishes to you!

g.

---

