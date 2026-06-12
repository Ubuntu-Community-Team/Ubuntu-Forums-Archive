---
title: "XBMC - Anyone Tried It?"
date: 2012-02-27
forum: Apple Hardware Users
---

### Post by svtguy88 on 2012-02-27
Anyone here used XBMC (Xbox Media Center) at all?  I use it on my Xbox, and am working on getting it installed on my Powermac/Lubuntu setup, however, PPC isn't technically supported.

After playing with the ./configure line (you must compile from source for PPC), I get it to build and install, but have some graphical issues once running the program.

Anyone else using it that can comment?  I'm assuming probably not, as there isn't really anyone on PPC on the XBMC forums either, but thought it would be worth a try here...

---

### Post by Double.J on 2012-02-27
Hi there Pkmgarf,

Just had a look over on the XBMC forums myself for you (I've not tried this media centre.)

To be honest it doesn't look good - seems that over the last 3-4 years, with various versions of XBMC people have managed to get to the same stage as you - compiled and running but with very high CPU usage, graphics glitches in the player and playback, but no-one seems to have found a work around.

I kind of suspect this may be the answer - the support for PPC development is really limited now they're getting on - my eMac is 9 years old in june! For smaller projects the resources needed to keep developing for a platform whose user base continues to decline exponentially each year just isn't feasible, and the hardware is getting really out of date - I've over clocked my G4 to 1.4Ghz but it can only do 32Mb of graphics!

Fortunately PPC versions of Ubuntu have continued for now, though I must admit I fear that 12.04's 5 year support may outlast my emac now. I really love the old box, but it may soon come the day to retire it :(

If you do find a way to get good performance out of it please keep us updated as I do like to keep my G4 and G5's running :)

---

### Post by svtguy88 on 2012-02-28
Thanks for the reply.  If you have been perusing the XBMC forums, you probably stumbled on my post (my name over there is 'svtguy88') about compiling from source on a G4.

I've narrowed (or believe I have) the problem down to XBMC's DVDPlayer, which is the main player for video files.  I can play all of my video files outside of XBMC fine (using mplayer or whatever), but there are problems when XBMC plays them.  If I use an alternate player (you can enable external players for XBMC to use), the videos play fine, so I think it's definitely XBMC's DVDPlayer.  My problems go away entirely if I switch to software rendering for video...but CPU usage skyrockets.

I see no reason that it shouldn't work.  There's a PowerPC version of XBMC for OS X.  I guess I'll have to dig out my copy of OS X, install and see how it behaves there.  I mean, if there's PowerPC code that works in OS X, why not in linux?

---

