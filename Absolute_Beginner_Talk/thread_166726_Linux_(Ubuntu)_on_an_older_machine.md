---
title: "Linux (Ubuntu?) on an older machine"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by lo_mein_dreams on 2006-04-27
I'm looking to install some form of linux on my 233mhz tablet pc with 98 megs of ram. It is a Fujitsu Stylistic 2300. Hard drive space is not an issue, I got a great deal on an 80 gig laptop drive, so this thing is sitting pretty on that front. But I am having overall slowdown issues running Ubuntu 5.10, even with Fluxbox. I mean, its not unusable, but I'd like it to be faster than the 98 currently installed. 

Any help with what to do with the current install, or a different distro would be appreciated. It doesn't have to be Ubuntu, but I'd prefer it to be Debian.

Thanks!

-Matt

(one other question: Why is it tha Xfce loads up faster for me than fluxbox. I find that a bit odd. Fluxbox does run better once its started though.)

---

### Post by Sef on 2006-04-27
> I'm looking to install some form of linux on my 233mhz tablet pc with 98 megs of ram.

Upgrade your memory should help.


> Any help with what to do with the current install, or a different distro would be appreciated. It doesn't have to be Ubuntu, but I'd prefer it to be Debian.


If you want another distro, debian-based DSL is the smallest distro.  Nondebian-based Puppy Linux is another good alternative.

---

### Post by bionnaki on 2006-04-27
ubuntu is probably way too heavy.
I recommend featherlinux, puppylinux, damnsmalllinux...
google 'em

---

### Post by IYY on 2006-04-27
It could be a good idea to install Ubuntu Lite instead of Ubuntu. It's a new IceWM derivative targeted at machines just like yours.

There is a bug with Fluxbox that makes it slow to load. It can be fixed by adding the following line in the beginning of  .fluxbox/startup

export LC_ALL=C

I don't think it will be faster than Windows 98 though. At least not in certain aspects. For example, it will boot slower and apps will take longer to load. Windows 98 is much faster than pretty much any *nix of equal capabilities for several reasons, the main one might be the way it manages memory (which is also why it crashes so often).

---

### Post by wh0rd on 2006-04-27
Try Xubuntu:
[https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)

---

### Post by lo_mein_dreams on 2006-04-27
When I goto .fluxbox there is no startup, just init, keys, menu and slitlist.

Blah. Late. Sleep.

Thankyou all for your help! I'm downloading Ubuntu Lite and puppylinux (linux + puppies = yes. very yes.)

Edit: Oh yeah, and I bought a 128 meg stick of 133 ram. Sadly the thing doesn't support more :(

---

