---
title: "Security Probs??"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by cplspafford on 2007-06-12
[SIZE="5"]I am a newer ubuntu user.  I have been getting around by researching here and lots of googling.  What I was wondering was this, I saw a bunch of security alerts while surfing.  Should I be worried about this or is it something that gets fixed with automatic updates.  Thank you everyone for your time.[/SIZE]


_____________________________________________________________________________________________________

[SIZE="4"]A security issue affects the following Ubuntu releases:

Ubuntu 6.06 LTS
Ubuntu 6.10
Ubuntu 7.04

This advisory also applies to the corresponding versions of
Kubuntu, Edubuntu, and Xubuntu.

The problem can be corrected by upgrading your system to the
following package versions:

Ubuntu 6.06 LTS:
  libpng12-0                               1.2.8rel-5ubuntu0.2

Ubuntu 6.10:
  libpng12-0                               1.2.8rel-5.1ubuntu0.2

Ubuntu 7.04:
  libpng12-0                               1.2.15~beta5-1ubuntu1

After a standard system upgrade you need to reboot your computer to
effect the necessary changes.

Details follow:

It was discovered that libpng did not correctly handle corrupted CRC
in grayscale PNG images.  By tricking a user into opening a specially
crafted PNG, a remote attacker could cause the application using libpng
to crash, resulting in a denial of service.[/SIZE]

---

### Post by shae on 2007-06-12
> The problem can be corrected by upgrading your system to the
following package versions.

That is what that means.

---

### Post by starcraft.man on 2007-06-12
No piece of software is 100% secure. Errors are found and corrected in a timely fasion in Linux. You probably just found a security update bulletin, its nothing out of ordinary. Mac's get security updates too you know and none of their users panic.

Don't worry. IPtables is a strong firewall and sudo keeps most things from doing horrible damage. Just be smart browsing, thats how most infections get on PCs nowadays via a browser.

---

