---
title: "Trying to get my NIC to work"
date: 2005-07-27
forum: Absolute Beginner Talk
---

### Post by john14617 on 2005-07-27
I just installed Ubuntu on my IBM T22 laptop that has a mini-PCI NIC/modem card.  Ubuntu appears to detect it okay- if I do a lspci in a terminal, it shows up ...

3Com Corporation Mini 3c556B CarfBus [Tornado] (rev20)
3Com Corporation Mini PCI 56k  Winmodem (rev 20)

But under Device Manager, it shows up, but on the Device tab, for Device, it says Unknown (and for Capabilities it also says Unknown.)

Under System>Administration>Networking, there is no NIC at all.  It seems to see the modem connection but is not configured.

I think basically what is happening is it sees the NIC, but it does not know it is a NIC.  Does anyone know what to do to make it work?

/John ](*,)

---

### Post by majikstreet on 2005-07-27
[QUOTE=john14617]I just installed Ubuntu on my IBM T22 laptop that has a mini-PCI NIC/modem card.  Ubuntu appears to detect it okay- if I do a lspci in a terminal, it shows up ...

3Com Corporation Mini 3c556B CarfBus [Tornado] (rev20)
3Com Corporation Mini PCI 56k  Winmodem (rev 20)

But under Device Manager, it shows up, but on the Device tab, for Device, it says Unknown (and for Capabilities it also says Unknown.)

Under System>Administration>Networking, there is no NIC at all.  It seems to see the modem connection but is not configured.

I think basically what is happening is it sees the NIC, but it does not know it is a NIC.  Does anyone know what to do to make it work?

/John ](*,)[/QUOTE]
 Maybe you need the drivers for the card.

Might want to have a look at [this page](http://tuxmobil.org/minipci_linux.html)

Or this [google search](http://www.google.com/search?q=3Com+Corporation+Mini+PCI+56k+Winmodem+linux+drivers&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official)

---

### Post by john14617 on 2005-08-02
[QUOTE=majikstreet]Maybe you need the drivers for the card.

Might want to have a look at [this page](http://tuxmobil.org/minipci_linux.html)

Or this [google search](http://www.google.com/search?q=3Com+Corporation+Mini+PCI+56k+Winmodem+linux+drivers&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official)[/QUOTE]
 On further research, I've seen that others have had horrible luck with this same model card.  I gave up on this system and am instead going with a different system.

---

