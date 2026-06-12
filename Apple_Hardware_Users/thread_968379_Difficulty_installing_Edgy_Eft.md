---
title: "Difficulty installing Edgy Eft"
date: 2008-11-02
forum: Apple Hardware Users
---

### Post by Lurcher on 2008-11-02
I have Dapper Drake (ubuntu 6.06) installed on an iMac G3/500, and have wanted to upgrade.  I understand that support by Canonical has stopped for the Power PC platform, though it is still being supported by the volunteer community.

Tbs, I cannot seem to install Edgy Eft (ubuntu 6.10).  I have burned two disks, and with difficulty have been able to start up from the Edgy Eft disk, though no installer appears with the image of the Edgy Eft disk, so as far as I know I cannot actually install it.

I am confident my burn (the second, the first acted in the same manner) is OK, though I cannot install.

Any help is, of course, appreciated.

---

### Post by mkvnmtr on 2008-11-02
I don't believe there is any support for 6.10. The next long term support destro is 8.04. You should be able to upgrade to 6.10 or 8.04 from your update manager. On my powerpc G4 I was not able to. I had trouble getting 6.10, 7.04 and 7.10 live disks to boot also. It was fairly easy to get the 8.04 live disk to boot and the install went fine. I believe what I had to do was hit the tab key when it first started to load  the kernal. This brought up a page with a lot of options. I think the one I used was linux video=ofonly nosplash. You have to type that in it will show at the bottom of the page. Then press enter. If you really want 6.10 you should be able to do the same thing but the option that works may be different. There will be no updates for 6.10 so you really should go to 8.04. Like always you should back up every thing you need to save.

---

### Post by Lurcher on 2008-11-05
Thanks for the assist.  Currently my computer attempts to upgrade, but it never completes.  I will try to download and install it instead.

---

### Post by Lurcher on 2008-11-09
I find ubuntu very interesting, but find the difficulty of installing (and upgrading) problematic.  Currently I am trying to install Hardy Heron, but like Edgy Eft, cannot do so.

I understand that Canonical does no longer support the PPC platform but if you have to almost literally contort yourself into a pretzel to do so, why would you want to.

Currently my primary platform is an iMac (OS 10.5.5) and would like to learn more about Ubuntu, but find the difficulty in upgrading on my iMac G3/500 very, very frustrating.

Currently I cannot boot from the Hardy Heron disk I have made, though it does mount on my desktop.

I should mention that I am double-clicking on the Hardy Heron disk image after downloading, then burning a disk from the expanded image.

I assume that I am doing this correctly (since as I mentioned, the Hardy Heron download does mount, though no installer appears) though if anyone has any questions about how I am proceeding I will do my best to answer them.

As usual, thank you for your support.

---

### Post by stream303 on 2008-11-10
> **Lurcher said:**
> I find ubuntu very interesting, but find the difficulty of installing (and upgrading) problematic.

We'll try our best...

> I understand that Canonical does no longer support the PPC platform but if you have to almost literally contort yourself into a pretzel to do so, why would you want to.

I feel your frustration.  Canonical actually does support the PPC platform, but not commercially.  That is, you cannot buy support contracts for it, and any bugs in the release will not hold up the official releases for X86 / AMD64 etc that you can buy contracts for.  Essentially this means that it is a community-supported, much like Debian and others that don't accept contracts. :)  Releases are still being made, and the software repositories are available.

Yet, the real gist is probably why isn't there better hardware support for PPC?  Because it is not in Apple's interest to be PPC Linux-friendly - actually, since OSX is so closely coupled to the hardware, much of the installation relies upon internal databases or hardware capabilities, rather than relying solely upon generic hardware probing.  This is one reason why you can't "downgrade" back to a version of OSX that is older than what it came with.  A lot of the hardware just isn't required to provide full probing feedback to other operating systems - which means that the Linux devs for PPC have to make do with the meager hardware documentation available, and sometimes the user has to make manual configuration changes on their own to force the hardware to work.

In addition, the PPC installers can't always detect the variations among machines.  For instance, your G3/500 has an Apple firmware limitation of the root partition which can't go beyond 128gb.  You can divvy up the rest of the disk of course, but the standard installer will choke unless you take the reigns - and have the knowledge beforehand to do so.  And to be safe, make it 125gb.  But that's what the community of like-minded users who have contemplated throwing their PPC macs through the window in year past are here for. :)

As for burning, the easiest way to burn the image as an iso, is to bring up OSX disk-utility, and then drag the Ubuntu iso image into the left-hand pane.  Highlight it, and then click burn.  If you can find a way to lower the speed to say 2X or 4X, then that is preferable.  CD-R recommended.

Thing is, I'll assume you'll want to dual-boot, and this would mean either reformatting your disk to make space for Ubuntu, or shrinking the hfs partition.

It can be done, but I'll admit that right up front it is going to seem like a LOT of work with no guarantees, especially if this is your first foray into Ubuntu / Linux.

So rather than let this be a black-eye for Linux, just chalk it up to having a system that wasn't designed to be friendlier than to anything other than OSX.  Personally, I'd stick to 10.5 for now, and enjoy other gnu software like gimp, firefox, OpenOffice, etc.

I don't want to drive your interest away, but just want to expose the realities of the situation - and I don't want to see the iMac get thrown down the stairs.

---

