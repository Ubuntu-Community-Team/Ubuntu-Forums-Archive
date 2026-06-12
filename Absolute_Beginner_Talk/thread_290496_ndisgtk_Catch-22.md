---
title: "ndisgtk Catch-22"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by HamCoder on 2006-11-01
When packages get downloaded as part of the install, where are they stored?  Can I copy a package to a USB Drive, take the USB to another PC and install the package from there?  How do I point the 2nd PC's Synaptic to the USB drive?  Point me in the right direction and I can probably do this.

Background:
I just installed 6.10 on top of 6.06 onto a Thinkpad 600x laptop.  I lost my wireless connections but was able to restore them because the laptop has both wired and wireless cards.  Now I have fast ethernet with the wire and medium with the wireless.

Then I installed 6.10 on top of 6.06 onto a desktop PC.  I lost my wireless connections again.  BUT... this PC has no wired connections and it isn't feasible to run Cat5 all over the house to make it wired.  This PC has ndis-wrapper but not ndisgtk.  iwconfig finds drivers and hardware.  No led's light up on the PCI card.  

If this were Windows, I could use a USB drive to transport the package from the laptop to the PC and get ndisgtk installed.  Apparently, 2 months of Ubuntu usage doesn't equate to years of Windows knowledge. (grin)

Thanks for the help.

--HamCoder

---

### Post by Dr. Nick on 2006-11-01
[http://packages.ubuntu.com/edgy/net/ndisgtk](http://packages.ubuntu.com/edgy/net/ndisgtk)
 
That site has a download to ndisgtk, and any dependencies if needed.
 
Just copy the .deb to a usb and take it over, simply double click it and it should install without having to reconfigure synaptic

---

### Post by HamCoder on 2006-11-01
That's simple enough that even a mainframe dinosour like me should be able to do it.  I'll let you know how it goes tonight when I get home and try it.

--HamCoder

---

