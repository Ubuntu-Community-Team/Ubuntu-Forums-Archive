---
title: "Maybe ndiswrapper for C2D AR5008 support on last ndiswrapper"
date: 2007-04-30
forum: Apple Intel Users
---

### Post by Azathoth_ on 2007-04-30
Looking for it, i have found this: Support for 64 bits in 1.43 ndiswrapper
[http://ndiswrapper.sourceforge.net/joomla/?title=Special:Recentchanges&feed=atom](http://ndiswrapper.sourceforge.net/joomla/?title=Special:Recentchanges&feed=atom)
Can anyone test it on a 64 bits version?

---

### Post by ronocdh on 2007-04-30
> **Azathoth_ said:**
> Looking for it, i have found this: Support for 64 bits in 1.43 ndiswrapper
[http://ndiswrapper.sourceforge.net/joomla/?title=Special:Recentchanges&feed=atom](http://ndiswrapper.sourceforge.net/joomla/?title=Special:Recentchanges&feed=atom)
Can anyone test it on a 64 bits version?
Sure, I could late tonight. However, I don't see what made you think the 64-bit support was new; what catches my eye is the:
> * Fixed long standing memory allocation issues with some drivers, Atheros especially. With this fix, Atheros cards in Macbook with Core 2 Duo are known to work
Now that's what I'm talking about! But this should work fine in either i386 or 64-bit Ubuntu. =/

---

### Post by Azathoth_ on 2007-04-30
> **ronocdh said:**
> Sure, I could late tonight. However, I don't see what made you think the 64-bit support was new; what catches my eye is the:

Now that's what I'm talking about! But this should work fine in either i386 or 64-bit Ubuntu. =/

I think the problem about 64 bit drivers and ndiswrapper is about a memory issue, but i'm not sure

> * Fixed long standing memory allocation issues with some drivers, Atheros especially. With this fix, Atheros cards in Macbook with Core 2 Duo are known to work

Ndiswrapper works some time ago with C2D macbooks atheros chipsets but now it says: "With this fix, Atheros cards in Macbook with Core 2 Duo are known to work" i think it means 64 bits also

---

### Post by ronocdh on 2007-04-30
> **Azathoth_ said:**
> I think the problem about 64 bit drivers and ndiswrapper is about a memory issue, but i'm not sure



Ndiswrapper works some time ago with C2D macbooks atheros chipsets but now it says: "With this fix, Atheros cards in Macbook with Core 2 Duo are known to work" i think it means 64 bits also

Well I have i386 on my book tonight, but I hate it :twisted: so I'll try on that just for testing's sake and then burn it to the ground and try on 64-bit.

---

### Post by ronocdh on 2007-04-30
Edit: Removed link; I hadn't read the thread carefully and it doesn't apply to the case at hand.

---

