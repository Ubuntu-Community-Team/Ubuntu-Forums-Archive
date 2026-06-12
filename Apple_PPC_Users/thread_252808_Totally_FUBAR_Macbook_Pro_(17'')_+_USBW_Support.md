---
title: "Totally FUBAR Macbook Pro (17'') + USBW Support"
date: 2006-09-07
forum: Apple PPC Users
---

### Post by Huehuecoyotl on 2006-09-07
After about four weeks of putzing, finagling, and more hours of "Google it" than I care to count, I've finally caved in to seeking assistance from total strangers who (likely) can offer the insight I need. There's a fairly large list of issues I'm having, trying to run Ubuntu 6.06 (or Linux in general) on my Macbook Pro. If needbe, I can edit this topic and split its contents into their proper forums, at moderator request.
Any specifications are available on request.

Ubuntu 6.06, installed along with rEFit (I believe the guide was from this forum), work**ed** nearly flawlessly. I ended up installing some packages, including Automatix et al. Altogether very pleased with its performance, though I'd never managed to get sound (or ATI's drivers/XGL-Compiz entirely) set up. Along the way, a friend introduced me to the wonderful world that is Kismet (and Ethereal). However, using an Airport Extreme, I was unable to get either program (nor its KisMAC cousin under OS X)to support passive monitoring.

So I spent some time studying up, looking around and trying other programs, and altogether learning about wireless networking and Linux. I stumbled upon a USB dongle which showed some promise (mostly because of its non-stick nature, and the fact it could be upgraded with a better antenna--DIY): Linksys's **WUSB54g** v4, Ralink chipset.

While this is supposedly compatible with Linux (+Kismet) and OS X, the Linux side was a complete and utter failure (and OS X only detects the device, no more). Using the Serialmonkey guides and such, I managed to get Ubuntu to recognize the device as "rausb0". It claimed to be active and configured.

Then I realized I had no wireless connectivity whatsoever, neither with the rausb0, or ath0 (Airport Extreme). Or my ethernet connection.

In the following days of trying to resolve this and undo whatever damage I'd managed to inflict in my bumbling, I noticed... In Terminal, while "sudo" worked without complaint, "su" consistently provided an authentication error. This problem has carried over to OS X, so I believe it's linked to my attempts to get the WUSB54g functional.

I had picked up a copy of Linux Format the day prior, with its special edition of Ubuntu (option-packed DVD). Having nothing left to lose, I simply formatted the Ubuntu partition and reinstalled the OS with this new DVD.

More failure. It boots up to the login screen, but the keyboard and mouse built in to the Macbook are totally unresponsive, and the screen itself locks up (requiring a hardboot) after <10 seconds.

At the moment I've been looking at reinstalling Ubuntu 6.06 the normal way (<3 Live CDs), Nubuntu, or <<Backtrack (which is Slackware based).

Now that the story's out of the way...

-Is there a Debian based distribution which works with the Macbook Pro without so many hardware conflicts? 

-Though I will be making a seperate thread specifically on this topic (though with some additional, specific questions), has anyone else tried to run security software like Kismet, Ethereal, or Ettercap _using their Macbook_? What dongle do you use that still allows rfmon (and, preferebly, packet injection)? I'm returning the WUSB54g, so I'm totally open to suggestions.

-What advisories, if any, should I heed extra attention to when tinkering with Ubuntu, due to its installation on a Mac? I.e. how can I prevent such spectacular screw-ups in the future?

Thank you. If additional information is needed, or this thread needs splitting, just ask. :)

EDIT: I understand there is a guide for installation of the WUSB54g dongle here at UF, but because of its involvement of the Ndiswrapper--and thus incompatibility with Kismet--I did not use it.

---

