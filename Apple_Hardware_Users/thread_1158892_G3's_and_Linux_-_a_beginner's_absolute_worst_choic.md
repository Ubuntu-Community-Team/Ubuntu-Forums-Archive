---
title: "G3's and Linux - a beginner's absolute worst choice."
date: 2009-05-14
forum: Apple Hardware Users
---

### Post by stream303 on 2009-05-14
I wanted to post this to just save *beginners* a LOT of time and frustration.

G3 Apple ppc computers, especially those with low memory at 256mb or below, are the absolute worst choice one can make to get working with linux, *unless you are already familiar with the problems, and have a designated purpose in mind, and the skillset to resolve hardware issues.*

You guys know me - I'll bend over backwards to help out, but we just have to face facts when it comes to low-memory G3's:

They have far too many configuration quirks, beyond the low horsepower and ram, to be anything but a mere technical exercise when all is said and done.  You'll go through a lot of pain just to end up putting it back on the shelf or in the shredder.

Most have cdrom drives that are failing, or are about to fail, making installation a nightmare - not to mention that to do it right, you have to burn an install cd at a very low speed like 1x - 4x, which some burners cannot even deal with.

Ok, so I'll boot from a usb stick - bzzzzt - wrong in most cases.  About the only thing you *might* be able to do if your cdrom is dead is boot from an external firewire cdrom drive.  Have one of those around?

As a beginner, you may not be aware of just how much you need to configure to get these sluggards up and running:

Some have newer hard drives in them that have an 8gb /root partitioning limitation.  Are you ready for manual partitioning?  Do you know how to identify your hard drive to know?  Do you know how to manually partition for the special apple partitions necessary before you even get to do a simple /root and swap?

ALL G3 iMacs will not have the correct configuration for the X gui.  One has to go back into the /etc/X11/xorg.conf and manually edit in special horizontal and vertical frequencies, not to mention messing around with video driver specs.

Just jumping to another distro isn't the solution, since the Apple quirks are common among all the distros - that is, Apple hardware is only designed to talk to OSX, and Linux is left begging for setup info which it doesn't get - so the installer just defaults to values that don't work.  Not Linux' fault!

Some distros like to add little niceities like a splash screen (Ubuntu), which cause problems right off the bat, and if they don't just lock the machine up,  are just a mess of weird colors and graphics.  Yet another issue to fix before you even get to the good stuff!  (note - no splashscreen to deal with in Debian)

What is your own personal limit for frustration?  Better have a lot of it.  Unfortunately for some, Linux on a G3 is their very first experience, and might think badly of Linux for not somehow getting things right or blame the devs, or think it is because the port is "non-official".  Please don't - the installers have NO WAY of automatically detecting these special Apple quirks beforehand.

(The ONLY way they could is if the installer adopted a database of known issues based on model detection, and overrides the typical default settings.  Don't count on this happening to a port architecture that hasn't been produced in the last 5 years - a nice pipedream maybe.)

The ONLY thing an old G3 is good for is if you *are already familiar with how to manipulate a Linux installation,* and know how to put up with the low-resource limitations, ie running just a server, a VERY minimal X with light applications, etc.  Of course, this is kind of like credit - to get the experience, you'll need to jump in.

Just "trying out" that old G3 laying in the corner is a mistake - UNLESS you KNOW you are only going to be doing it for the technical exercise.  But if this is the case, you'll have to do a lot of homework first.

Let's take a typical 400mhz G3 with 128mb of ram.  Would you expect anything from an 800mhz PC running Ubuntu with only 128mb of ram?  (with g3's you double the cpu freq for a rough comparison to other pc's)  AND throw in the numerous Apple quirks, possibly not knowing how to use a text-based editor the firt time out to fix it?

I'm sorry guys - I just can't deal with G3 issues any longer.  It has been fun, and you know I certainly don't hold it against anyone wanting to try - but at some point, hardware has to match reality.

---

### Post by Benboom on 2009-05-14
Yeah, I have two old beige G3 minitowers here and after reading up on what was involved I decided to leave them just as they are. :D

---

