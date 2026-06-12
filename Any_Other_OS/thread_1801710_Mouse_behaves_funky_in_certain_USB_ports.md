---
title: "Mouse behaves funky in certain USB ports"
date: 2011-07-10
forum: Any Other OS
---

### Post by Caleb9849 on 2011-07-10
Hi all,

My system acts strangely with my wireless Logitech LX7 mouse if I have the receiver plugged into certain USB ports.  It seems to be fine in the front ports, but usually not the back ports.  If I have it plugged into one of the back ports (which I'd like to do, as it looks ugly sticking out of the front of the machine :P), it works fine for a few minutes, but eventually the mouse will suddenly fail to have any sway with specific, randomly-chosen parts of my interface.  The interface is very specific about what will work and what won't.  For example, my panel may stop responding to the mouse.  Or the contents (application) in a particular window.  Or the window decorations / control buttons.  One or two or all three of these things will stop responding to the mouse all of a sudden, even though the mouse is working fine otherwise, and the interface component which stops responding to the mouse is still running just fine, and will respond to keyboard input, if applicable.  Example: suppose Pidgin decides to stop responding to the mouse.  If I was lucky enough to have the focus in the text box where I type to my friend, I can still communicate to my friend, but I cannot change focus (except by TAB and SHIFT+TAB) or click on a tab for a different friend!  :P  It's rather bizarre.  If the problem is occurring, I can remedy it by removing the mouse receiver and plugging it into a different port; I get all mouse functionality back immediately, but I don't like to have to do this, and in particular I don't want to have to have the receiver plugged into the front of my machine all the time, if I can avoid it.  I've been looking around for help with this and the theory of an IRQ conflict has arisen.  Here are my USB IRQs from /proc/interrupts:

 17:          0         11          0         23   IO-APIC-fasteoi   ehci_hcd:usb1, ehci_hcd:usb2, ehci_hcd:usb3
 18:        778      39379     314868        257   IO-APIC-fasteoi   ohci_hcd:usb4, ohci_hcd:usb5, ohci_hcd:usb6, ohci_hcd:usb7, nvidia

Note that my video card is getting the same IRQ as four of my USB controllers -- the 1.1 ones.  The other three controllers, 1, 2, and 3, are apparently the 2.0 controllers.  The mouse always gets an IRQ 18 controller no matter which port I plug it into (since mice are rarely if ever USB 2.0, AFAIK), so the mouse is getting the same IRQ as the video card, even with the front USB ports.

I don't know for sure whether or not this is an IRQ issue.  I'm on a fresh installation of Mint 11 Katya, and my hardware is a very recently self-built machine.  That NVidia card is a Gigabyte card with an NVidia GTX 260 chip.  Any other information is readily available.  Can anyone offer me any insight into this weird problem?  Thanks in advance!  :)

---

### Post by Perfect Storm on 2011-07-11
Moved to Other OS/Distro Talk.

---

