---
title: "BIOS bug 8254, No internet connection, Can't access floppy drive"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by paulholbrook on 2007-04-27
I am trying to migrate from Windows XP to Ubuntu 7.04.  When I boot the liveCD I see this message flash on the screen:
MP BIOS Bug 8254....

Ubuntu does load and I can execute the spreadsheet and the word processor but Firefox tells me it can't find the server.  It appears I am not connected to the internet.

Also, I cannot access my floppy drive that is attached via UCB.

I am running on a desktop Compaq AMD Sempron 3200++ desktop and using Verizon FIOS hardwired internet.

I am new to Linux.

---

### Post by st33med on 2007-04-27
Please put out your lspci and dmesg output here. If you don't know how, just go to, Applications->Terminal and type lspci and, afterwards, dmesg.

And welcome to the community of Ubuntu, where Coffee beans are the worth the same as Britney Spear's songs :D

---

### Post by Najand on 2007-04-27
Go to BIOS and try disabling IOAPIC
if there was no option there, when using live cd, press F6 and try adding the "noapic" option before the final -- in the text line with boot options.

So your line should something look like:

```

xxxxxxxx xxxxx xxx xx xxx xxxx noapic--

```

---

### Post by Najand on 2007-04-27
> **st33med said:**
> Please put out your lspci and dmesg output here. If you don't know how, just go to, Applications->Terminal and type lspci and, afterwards, dmesg.

And welcome to the community of Ubuntu, where Coffee beans are the worth the same as Britney Spear's songs :D

Does it mean the beans are that cheap?

---

### Post by st33med on 2007-04-27
Yeah, I just go onto eBay and buy them for 5 cents a piece, hoping I'm not being sapped:popcorn: 

Anyways, that was quoted from a comedy show called 'Who's Line Is It Anyways?' Drew usually compares the worth of points to something worthless^^

---

### Post by paulholbrook on 2007-04-27
I will have to go learn how to do those things but I will give it a try.

Thanks.

---

