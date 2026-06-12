---
title: "Dual Monitors, two graphics cards. Help?"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by zerhacke on 2006-05-22
I am trying to do something but I just can't seem to find out how to do it.  I've searched the forums and google.  While I've found CLOSE things, nothing I've found exactly matches my setup.

I've got two video cards in my computer.  One is the onboard Intel I810 and the other is a PCI nVidia TNT2 Ultra using the nv driver  - for some reason if I install the nVidia drivers on it it dies.

The i810 onboard is connected to a Compq 1024 15inch monitor.  The nVidia card is connected to an HP v70 17inch monitor.

How do I get the second monitor to work?  I've tried everything I could think of, including Xorg -configure.  It configures the first card/monitor perfectly, but it doesn't include the second video card/monitor at all.  Optimally I want the card to span desktops from one to the other, not copy the first desktop to the other.

Any help?

---

### Post by zerhacke on 2006-05-22
Did a little more digging.

How do I find the BusID of my video cards?  I believe I need them in order to get the second monitor working.

---

### Post by halfvolle melk on 2006-05-22
```
lspci -X
```
gives the output that dpkg-reconfigure xserver-xorg would want.

---

### Post by zerhacke on 2006-05-22
lspci -x gave me a bunch of stuff I don't understand.  lspci without the -x gave me a more understood output, but I still don't understand what I'm supposed to do with it.

dpkg-reconfigure xserver-xorg walked me through reconfiguring Xorg again, but specifically stated that it won't do mutliheaded displays.  Told me I'd need to edit xorg.conf by hand to get the multiheaded part working.

I'm still at ground zero.

---

### Post by halfvolle melk on 2006-05-23
[QUOTE=zerhacke]lspci -x gave me a bunch of stuff I don't understand.[/QUOTE]
Neither do I ;). Try lspci -**X**.

edit:
Maybe this helps a bit
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

---

### Post by zerhacke on 2006-05-23
Followed the link you gave, thank you for that.

However, I found that the second video card, the nVidia card, is blown.  It will not configure properly.  I stuck it in my daughter's Windows machine and it doesn't work.

Back to the drawing board.  Thanks for the info you provided to me.

---

### Post by bistros on 2006-06-07
I would not be so hasty about writing off this adapter.  There is an obvious, real duplicable, repeatable problem with dual monitor / dual adapters on Dapper right now.  I've tested thoroughly, and I'm not a noob (I've been contracted as an engineer by LPI to review the Ubuntu certification testing questions).

There is a problem with libint10.so in Dapper where it fails to retrieve V_BIOS information from secondary (and tertiary ...) cards in this situation.  This causes Dapper to unload modules for the second (and third ...) adapters.  It may be a problem with the i810 modules that propogates forward - there is lots of incidental evidence out there that the i810 may be related.  I've got logs, dmesg output and repeatability.

The only consistent google'd evidence I've seen of successful dual (or more) headed installations working in Dapper are those using proprietary binary drivers for NVidia or Intel.  I've tested with the i810 driver, the ati driver, the nv driver, and the nvidia (binary proprietary) driver.  

I've altered the motherboard video priority, altered the bus slot, altered configurations of combining the i810 and others - every case causes failure in the same place regardless of the driver involved - the second card loaded fails at the libint10.so load.  X reports finding all the cards I've tested, and has confirmed the PCI bus ID's detected match the hardware settings in the xorg.conf file.

The exact same base dual monitor / dual video card hardware configuration worked fine in Breezy - it is not a untested combination.

I've manually edited xorg.conf to match the hardware reports in dmesg and lspci - I've reviewed the X.0.log - everything points to a fundamental problem with libint10 - especially when there is an i810 embedded video controller somewhere in the local food chain.

I've also performed an automatic detect "X -configure" - it still consistently fails.

I've filed a bug report on launchpad, and offered to help, but had no response.  I don't know what I've got to do to get the good folks who can fix things to notice!

--
Bill Strosberg

---

### Post by JohnnyLee on 2006-06-08
I have a similar problem with two cards: an APG and a PCI radeon 9200. X fails to start with the second card saying it can't read the V_BIOS. This was a working configuration on Breezy and Hoary.

---

### Post by rdejean on 2006-07-24
bistros,

I am having the same damn problem.  Also not a n00b, been running debian sid for years.  Tried all the things you've tried.  I see novell has released new x.org rpms to fix this.

[https://bugzilla.novell.com/show_bug.cgi?id=171453&x=20&y=6&=Find](https://bugzilla.novell.com/show_bug.cgi?id=171453&x=20&y=6&=Find)

Have unbuntu released a fix yet?

ray

---

