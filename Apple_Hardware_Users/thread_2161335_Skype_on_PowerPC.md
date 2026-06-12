---
title: "Skype on PowerPC?"
date: 2013-07-10
forum: Apple Hardware Users
---

### Post by copyandpaste on 2013-07-10
Hello,

i'm running Lubuntu 12.04 on my eMac (PowerPC).
As far as i know there is no PPC build of Skype. So i tried to install (and also force install) the "Ubuntu 12.04 (multiarch)" version, but i'm getting a "wrong architecture" error.
Is there any possibility of installing Skype? Is there something like a x86 emulator for PPC?

Thank you in advance for helping...

p.s.: And no, i don't want to install any Mac OS on my eMac (now that it's a freeMac :))

---

### Post by rkmugen on 2013-07-10
The ([PowerPCFAQ]("https://wiki.ubuntu.com/PowerPCFAQ#What_software_is_available_for_PowerPC.3F")) states that there are notable absences of popular apps for the PPC architecture, with Skype being one of them.  And, according to Skype's Wikipedia entry, Skype:> ...was bought by [Microsoft]("http://en.wikipedia.org/wiki/Microsoft") in 2011 for $8.5 billion.

Though Skype's protocol has been reverse-engineered ([http://skype-open-source.blogspot.com/2011/06/skype-protocol-reverse-engineered.html](http://skype-open-source.blogspot.com/2011/06/skype-protocol-reverse-engineered.html)), according to Lubod's post on the MintPPC forums ([here]("http://www.mintppc.org/forums/viewtopic.php?p=5630&sid=e519e01f9a5c8d21e8754cff9fbbe0a6#p5630")), it seems that Microsoft has broke backwards compatibility with the older protocol, so presumably, any attempt to make a PPC-compatible binary for that old Skype protocol simply won't work with whatever protocol all the other Skype users are using currently.

I doubt Microsoft would want to have any interest in helping more people get onto Linux.... even if they're using old Mac hardware (pure spite).

---

### Post by copyandpaste on 2013-07-14
Thank you for this information.

I would like to test the reverse-engineered Skype (having a chance of getting this in-your-face-microsoft-feeling is quite tempting), but that means i have to learn how to compile a Debian package for PPC from source... maybe mañana..... 
If ever i'll try to install the "open-source-skype" AND if it's working i'll let the PPC comunity know.

And if anyone has Skype running on PPC, please let me know how!

p.s. i realized that 700 Mhz and 512 Mb RAM is not the best condition to use a x86 emulator

---

### Post by lubo2 on 2014-04-08
I realize the last post in this thread is a year old, but maybe if someone else reads it later it may add some information, even though I don't have any surefire solutions (yet?). I'm the lubod quoted by [rkmugen]("http://ubuntuforums.org/member.php?u=1801984") above. ANd while my post about the consequences of the Microsoft Skype buyout are somewhat biased, they are as far as I know factually correct, insofar as it is possible without insider info. of which I have none.

I had an idea (or two) which is just crazy enough it might work.

Get the sources for Qemu, [here]("http://packages.ubuntu.com/source/trusty/qemu").
Compile (static if possible) on PowerPC. You don't need it all, just the qemu-user-i386 and qemu-system-i386, along with some of the accompanying utilities to create/modify disk images (qemu-img, and so on).
If you get qemu-user-i386 (and/or qemu-system-i386) binary that runs on Linux PowerPC, run Skype Linux x86 (maybe the static build) on top of qemu.

Otherwise it's time to break out Wireshark, and other network admin goodies and try to reverse engineer the current Skype protocol, if neither the prospect of being sued into oblivion by Microsoft or having it break again when they release a new version dissuades you. Both prospects dissuade me, to some extent.

P.S. As long as I've put this thread on life support, try and test the PowerPC build of Trusty (with your desktop environment of choice, e.g. xfce, lxde, etc.). And file bugs, so it gets fixed. I'm doing that with the i386 build, because my PowerPCs aren't with me at the moment, but I'd still like to see the PowerPC port do well, it is one of the most useful general purpose OSes for the platform still being updated.

---

