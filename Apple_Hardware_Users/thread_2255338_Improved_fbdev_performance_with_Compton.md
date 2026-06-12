---
title: "Improved fbdev performance with Compton"
date: 2014-12-04
forum: Apple Hardware Users
---

### Post by dand1972 on 2014-12-04
Hi,

This is for radeon users who can't use KMS and are stuck with the fbdev driver (i.e., if you use the boot parameter "video=radeonfb:1024x768-32").  I noticed in Debian Jessie that window-dragging improves considerably under the fbdev driver when using the compositor Compton.  If you load it with "compton -b" it runs as a daemon.  Using the native compositor in XFCE also improves speed, but not as much.  Can anyone confirm this in Lubuntu or Xubuntu?  I don't have a 'buntu installed at the moment.  I'm between relationships ;)

---

### Post by rsavage on 2014-12-12
> **dand1972 said:**
> 
I'm between relationships ;)

Then let me introduce you to Ubuntu Mate - [https://plus.google.com/111285327879595317710/posts/2dTTB6qBHrA](https://plus.google.com/111285327879595317710/posts/2dTTB6qBHrA)

---

### Post by este.el.paz on 2014-12-12
> **dand1972 said:**
> Hi,

This is for radeon users who can't use KMS and are stuck with the fbdev driver (i.e., if you use the boot parameter "video=radeonfb:1024x768-32").  I noticed in Debian Jessie that window-dragging improves considerably under the fbdev driver when using the compositor Compton.  If you load it with "compton -b" it runs as a daemon.  Using the native compositor in XFCE also improves speed, but not as much.  Can anyone confirm this in Lubuntu or Xubuntu?  I don't have a 'buntu installed at the moment.  I'm between relationships ;)

@dand:

Thanks for posting this, indeed, in my iBook with a radeon driver, window dragging is less than ideal . . . been struggling with other issues in 14.04, haven't had a chance to think about how I could test out your idea . . . .

> **rsavage said:**
> Then let me introduce you to Ubuntu Mate - [https://plus.google.com/111285327879595317710/posts/2dTTB6qBHrA](https://plus.google.com/111285327879595317710/posts/2dTTB6qBHrA)

@rsavage:

Thanks for sharing, I like MATE . . . using LM17 MATE in my MBPro . . . you know what I'm going to ask, right?  Does it have a working "suspend" or can it revive from "hibernate"???  : - )

e.e.p.
[Edit: Rainy morning in LA, snagged the item, could not get the USB stick to boot on my iBook using the option key, have to try later; burned it to DVD, had to use "live-nosplash-powerpc video=ofonly radeon.agpmode=-1" to get into a clear desktop . . . looks nice.  I definitely like the "floating feet" screen saver that MATE offers . . . I do like the LXDE desktop that goes with the Lu 14.04 install I've been working on various issues . . . .  I might try to just add the MATE DE to my present install, so I wouldn't be going back to ground zero . . . getting 14.04 set up to run on my iBook--the agp thing, the xorg.conf file, the problem with not being able to login to my user account after an update, etc.  

But, to answer my question, suspend did work, the floating MATE symbol started up, very amusing . . . but when reviving back the time setting was again erased . . . .  Anyway, thanks for sharing this . . . looks like a worthy alternative for PPC users.]

---

### Post by este.el.paz on 2014-12-22
> **dand1972 said:**
> Hi,

This is for radeon users who can't use KMS and are stuck with the fbdev driver (i.e., if you use the boot parameter "video=radeonfb:1024x768-32").  I noticed in Debian Jessie that window-dragging improves considerably under the fbdev driver when using the compositor Compton.  If you load it with "compton -b" it runs as a daemon.  Using the native compositor in XFCE also improves speed, but not as much.  Can anyone confirm this in Lubuntu or Xubuntu?  I don't have a 'buntu installed at the moment.  I'm between relationships ;)


@dand:

Been thinking about your post here for awhile, because window dragging in my iBook running Lu 14.04 has been "rough" . . . it happens, but quite jaggy.  So, yesterday I checked "lsmod" to see if I'm using fbdev on my iBook . . . but with the "agp.mode" boot params it showed "radeon" in various places . . . nothing about "fbdev" . . . .  I found "Compton" in synaptic, but since I'm not using fbdev I didn't just dive right in on it.

Instead I installed "xfce4" and suggested dependencies, so now I have "XF session" available . . . going to play around with that a bit to see how that goes . . . window dragging seemed marginally "better" . . . but far from "smooth and precise." 

e.e.p.

---

### Post by rsavage on 2015-01-28
For those using KMS (or radeon UMS using downgraded xorg/mesa packages) there is the old compiz..... [https://ubuntu-mate.community/t/powerpc-14-04-release-notes/68/2](https://ubuntu-mate.community/t/powerpc-14-04-release-notes/68/2)

---

