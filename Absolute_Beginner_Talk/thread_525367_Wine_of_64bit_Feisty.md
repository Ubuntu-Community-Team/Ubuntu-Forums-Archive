---
title: "Wine of 64bit Feisty?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by martialartist81 on 2007-08-14
Hey, did a search on this in the forums, and nothing leaped out and smacked me, so I thought I would ask:

Is it possible to install Wine on 64bit version of Feisty?  I have an Intel C2D E6400 (Not AMD).  For whatever reason, in trying to download the package in Package Management, it keeps saying that it's for AMD 64 and I can't do it.  Uhhh...... huh?  I don't "want" the AMD version!  :0)

Any thoughts?  Should I switch back to the 32 bit version?  And if so, do I just download the LiveCD of that version and install it over my current or do I have to kill the 64bit and then install?

Thoughts, questions, suggestions, life-advice?

---

### Post by RomeReactor on 2007-08-14
Hi. AMD64 is the term to refer to 64 bit architectures, both Intel (IA-32 or EM64T) as well as AMD.

Regarding Wine, you're in luck! there's a [64 bit package for Feisty]("http://www.winehq.org/site/download-deb").

As for going back to 32 bit, if you don't have a substantial reason for using 64 bit, you should probably go for 32, as it has more supported applications and is more stable.

---

### Post by martialartist81 on 2007-08-14
> **RomeReactor said:**
> As for going back to 32 bit, if you don't have a substantial reason for using 64 bit, you should probably go for 32, as it has more supported applications and is more stable.

Awesome, and I will do.

Any special instructions for swtiching back to the 32bit version (i.e. uninstall 64bit, just livecd-install over the 64bit, or sacrifice small lambs)?

Just want to make sure I don't hose anything (at least not yet....).

Thanks!

Cheers

---

### Post by RomeReactor on 2007-08-14
Well, the only thing would be to back up any important data you currently have on the drive, by burning it to CD or DVD, or transferring it to USB. Other than that, just download the Ubuntu 32 bit image, burn it, run the Live CD again and install over the 64 bit.

---

### Post by martialartist81 on 2007-08-14
Wonderful.

As always, you guys Rock!

And Roll!

All day long!

---

### Post by Hospadar on 2007-08-14
most of your settings should transfer over to a 64 bit system just fine (all those hidden folders and files in your home directory) so you could burn all your data and all that stuff to a cd/dvd and then put them back onto your system.

You may want to put those config files back on one at a time so that if something screws something up you know what it is (and be sure to back up the default config files before replacing them.)

---

### Post by univremonster on 2007-08-14
> **RomeReactor said:**
> 

As for going back to 32 bit, if you don't have a substantial reason for using 64 bit, you should probably go for 32, as it has more supported applications and is more stable.

You might want to keep that 64-bit processor around, as Windows is planning on switching exclusively to 64-bit in the next few years and it seems that the people who write drivers are only concerned with Windows.  It may very well be that the 32-bit processor you go out and buy goes obsolete before the 64-bit you have!

---

### Post by RomeReactor on 2007-08-14
> **univremonster said:**
> You might want to keep that 64-bit processor around, as Windows is planning on switching exclusively to 64-bit in the next few years and it seems that the people who write drivers are only concerned with Windows.  It may very well be that the 32-bit processor you go out and buy goes obsolete before the 64-bit you have!

Actually, **martialartist81** is not changing processors; just the operating system, from a 64 bit architecture to 32 bit. Modern 64 bit processors can run in either mode.

---

### Post by martialartist81 on 2007-08-14
Oh, good lord no!  I LOVE, absolutely LOVE, my E6400 (64bit processor) Core 2 Duo.

This little puppy is a 2.16ghz stock, and I've already overclocked it to 2.66 (which is what the E6600 is at stock, and more expensive).  Orthos and Prime95 Stable overnight, without breaking over 58C under full load. 

I'm a pretty heavy PC-gamer so I have to keep Windows up and running (XP, and NOT vista).  So my performance in gaming, windows and linux is phenominal for a great price (helps that I bought good ram and other components, etc).

Soooo, back to the point:

Using the 32bit version is fine by me.  It seems (as per several thousands of postings that I've seen) that it has much better and more extensive support.  My main goal (for right now) is getting Wine up and running so I can play some of my games on Linux.  There's a few games that I won't be able to play in Linux period (i.e. Lord of the Rings Online, due to the launcher being scripted only for windows environment, however, there's the valiant group out there trying to get it to work, and work consistantly).  Now, the day that game can be run on either Cedega or Wine, I will drop Windows like a bad-habit, light my CD on fire, and dance around it wearing a grass-skirt, a giant sombrero and singing "Ding, Dong the Witch is Dead."

---

