---
title: "WEP security and Apple Airport Wireless Configuration"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Maxwell Rocatanski on 2007-03-05
Folks,

I've searched through the beginner's forum for the answer to this and I'm still coming up with a blank.  Forgive me if this has already been dealt with elsewhere, but I'm new to both Ubuntu and forum use.

In a nutshell: Running Edgy Eft on a Powerbook G4 Titanium, dual-boot with Mac OS X, using the original Apple Airport 802.11b card and an Airport (snow) base station (i.e. non-Extreme).  Everything connects happily if I disable WEP security on the base station.  When I enable WEP, Ubuntu cannot successfully request an IP.  Is there a definitive "how to" configure WEP security (i.e. ASCII vs. Hex, WPA vs. WEP, etc.) in Ubuntu running on a PPC platform?

I've added wifi-radar for more of a GUI control panel (I'm not yet as comfortable with terminal commands as I'd like to be).  The one piece of information that makes this so frustrating is that, prior to this installation, I had _only_ Ubuntu installed on this laptop (i.e. no dual-boot) and Airport (with WEP) worked like a champ, plug and play.  Somehow the addition of the Mac OS  boot partition changed the way Edgy handles wireless resources (it's the exact same build in both installs--same ISO source).  Is this a bug or am I missing something obvious?

Thanks in advance,

Maxwell

---

### Post by Maxwell Rocatanski on 2007-03-05
Just "bumping" this thread in the hopes that someone will respond...

Since nobody has responded yet, I went ahead and performed a clean install of Edgy Eft. Without updating a thing, Ubuntu cannot obtain an IP from a WEP-enabled Airport base station.  However, the same installation (unchanged, virgin install) worked flawlessly with my WEP-enabled Airport network when it was installed as the only OS on the laptop.  I can only conclude that _some_ aspect of establishing a dual-boot environment (Mac OS X.4 on the first HD partition, Ubuntu on the second) interferes with the native Airport network card.

I've been reading in the Apple PPC forum and the Wireless network forum and this inability to successfully negotiate a WEP-enable network seems to be a common, yet unresolved issue.

I'm a bit clueless when it comes to editing/extracting drivers and building resources in the terminal interface--if this is the only way to go, could someone please describe the steps involved?  I think this is a good candidate for a sticky.

Maxwell

---

### Post by jazz1 on 2007-10-21
I'm having a similar problem. I have an Airport Express and an Airport Graphite. On the Express I am running WEP 128. I have used both a PCI card and a USB Wifi adapters. 7.10 on my Dell Optiplex sees my two Airport hotspots, and when I plug in the HEX password it tries to join the wireless network. Somewhere I thought I read years ago that on Windows machines it helped to put a "$" in front of the hex key. This didn't work for me here.

I get three choices in the dialog box? Am I choosing the wrong one. I know my system isn't open. So that leaves two other choices. What is the correct choice for WEP 128. I've also tried the text password that works on my Apple laptop for this Airport Express. Still no go.

Right now I'm running a wired connection through a Squeezebox. It works fine but I am wondering if I'd get better performance a wifi adapter on my computer? Plus, I'd like to upgrade to a newer Dell, and of course would want that work without the Squeezebox acting as a router.

To make things worse I am thinking about an Airport Extreme, for an "N" connection.....that would be sweet!

---

