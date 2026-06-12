---
title: "Airport Extreme alternative - USB?"
date: 2005-08-15
forum: Apple PPC Users
---

### Post by JGaughran on 2005-08-15
Airport extreme appears to be difficult if not impossible to use in Ubuntu.  

As for an alternative, does anyone have any experience with any USB wireless devices that work well?  If i could find one at Best Buy or similar, that'd be best, since I'm impatient and would love to be able to go out and buy one instead of waiting for it to be shipped to me.


If it helps, I'm running a 12" powerbook G4 titanium.

---

### Post by slux on 2005-08-15
This has been previously discussed, but your best bet is probably to get something that has a Ralink [rt2570](http://rt2x00.serialmonkey.com/)  chip if you're after 802.11g connectivity. I haven't got experience running it on PPC though so the arch might be a problem. I do have experience running it on x86 (a PCI model) and the linux drivers are excellent, the machine has currently been up for 83 days and the connection has been flawless. The original driver source for these cards was released under the GPL. Another option could be prism54 but it's hard to find a card that is guaranteed to work as some of the later chip revision aren't working (and might never).

If 802.11b will suffice, you have more options. I've personally used a white Buffalo USB stick which works with the prism2_usb driver from the linux-wlan-ng package. That one doesn't use the standard iwconfig tools and is a bit tricky (not too bad) to set up though. I think the 802.11g version of the same Buffalo stick may use the ralink chip and could be a really good choice because of that.

---

### Post by JGaughran on 2005-08-15
Ahh, this is what I get for not searching well enough.  Thanks for your response, this should definitely get me what I need to know.

---

