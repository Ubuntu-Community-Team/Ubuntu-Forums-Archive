---
title: "is this a scam?"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by jonwatts on 2007-11-29
I'm trying to buy a cardbus wireless adapter that will work without much hassle in Ubuntu 7.10 on a Dell Latitude C640, and it would be really nice if the card had excellent range.

What would be most helpful is if you could click [HERE]("http://www.data-alliance.net/servlet/the-26/Zcomax-Zcom-300mw-Wireless/Detail") and tell me how it looks.

OR

here's my question:
about Linux, it says:
"Linux/UNIX driver & instructions provided on CD:  Supports all POSIX (Linux/BSD/UNIX-like OSes).  LINUX-based utility (provided on CD) allows operation in the following modes:  Infrastructure, ad-hoc, AP, "monitor mode."  Works with the HostAP driver and the Wlanng driver. All live linux distros come pre-loaded with these drivers however not all live linux distros have these drivers correctly patched/installed etc. - they are buggy.  It works perfectly on Auditor, Whax, Knoppix and Slax, but Slax needs the updated patched version of the driver.   Works with Auditor-Linux."

what does all this jibber jabber mean?

thanks!
jon

---

### Post by civic_si on 2007-11-29
Auditor WHAX and Knoppix are all live cd's so they may not be updated to have the drivers included.

---

### Post by jonwatts on 2007-11-29
why would a wireless card only work with live CDs?

---

### Post by reckless2k2 on 2007-11-29
if you are looking for a supported card out of box, look through the documentation directly from ubuntu:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

the info in the link you provided is dated due to the fact that a few of the distros are not even being maintained anymore for years in most cases. a few of those liveCD distros are specifically for penetration testing (hacking networks) so the specs talk about how that device can be put into various modes for injecting and sniffing reasons. that's what that jibber jabber is about. you are better off just reviewing the ubuntu support docs to find out what works. then google search and you'll be fine.

---

### Post by jonwatts on 2007-11-29
ok... thanks.  I was looking for a card with longer range than most, but i'll settle if its less of a hassle.  no more jibber jabber.

---

### Post by julian67 on 2007-11-29
The reason Auditor, Whax, Knoppix and Slax are mentioned is that they are often used for security/penetration testing and monitor mode is required for this (there are cards out there whose Linux driver does not support monitor mode so it's good that this is mentioned).  Auditor and Whax are distros specifically for testing. This looks like an ideal card for any distro. I'd buy one if I needed another wi fi adapter.

---

### Post by jonwatts on 2007-11-29
so I'm getting mixed messages here.  Any idea if this card would work out of the box for me?  Or if it would take a great deal of effort to get it operating?

---

### Post by sailor2001 on 2007-11-29
> **jonwatts said:**
> so I'm getting mixed messages here.  Any idea if this card would work out of the box for me?  Or if it would take a great deal of effort to get it operating?

that's the purpose of having a live cd so you can check all peripherals to be sure they can be configure

---

### Post by reckless2k2 on 2007-11-30
sorry you didn't get a clear answer. wlanng is prism2 driver i think. query the boards on it real quick but it's either supported out of box or you have to do a restricted drivers menu install similar to atheros chipsets. 

does that help?

as far as range, you might consider the WAP versus an adapter card. for instance, i had the version 1 belkin pre-N from some time back and that had THEE most amazing range of any router. they later came out with a version 2that stinks. you can't find the version 1 now except ebay pricey. and for good reason. it didn't matter what card you had, the whole block was picking up your AP. hahaha. SERIOUSLY. best range of anything i ever had and i test a lot of APs.

---

