---
title: "rtl8187 won't send email"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by Speedoo on 2008-01-14
Hi folks,
Here's my latest problem for your expert consideration:
I've been playing around trying to get my Realtek rtl8187 wireless adapter working better.  When I lost wireless connectivity entirely, I gave up and reinstalled Gutsy 7.10 to get back to the distribution supplied driver.  I now have wireless connectivity (with frequent dropouts requiring computer restart.)  However, I've found that outgoing emails frequently refuse to send.  It seems that I can send email at night, but not during the day (when I do most of my work from home!)  I can access the Web, and receive emails fine, but sending is problematic.  I thought it was a Thunderbird problem, so I configured Evolution and attempted to send from that, but again, I received email but couldn't send.  I went back to Thunderbird, plugged an ethernet cable into my laptop and router, and was able to send my email.  So it looks like it's a wireless issue.
I tried installing Cuervo's patched rtl8187 driver ([http://www.datanorth.net/~cuervo/rtl8187b/README](http://www.datanorth.net/~cuervo/rtl8187b/README)), which I had working on a previous install (2 or 3 installs ago) but this time I was unable to compile the driver due to "Unknown symbol in module" errors.
Then I tried installing ndiswrapper with the Win98 driver (also got this to work on a previous Gutsy install) but although ndiswrapper -l showed the driver and hardware correctly, I had no wlan0!  That's when I reinstalled Gutsy and got the provided driver working, but without the ability to send email during the day.
My router is a D-Link 802.11n connected to a cable modem from Comcast.
Thanks in advance for any help or suggestions.  I assume you'll need more info from me, but this post is getting kind of long and I'm not sure what else to provide.

---

### Post by dcstar on 2008-01-15
> **Speedoo said:**
> Hi folks,
Here's my latest problem for your expert consideration:
I've been playing around trying to get my Realtek rtl8187 wireless adapter working better.  When I lost wireless connectivity entirely, I gave up and reinstalled Gutsy 7.10 to get back to the distribution supplied driver.  I now have wireless connectivity (with frequent dropouts requiring computer restart.)  However, I've found that outgoing emails frequently refuse to send.  It seems that I can send email at night, but not during the day (when I do most of my work from home!)  I can access the Web, and receive emails fine, but sending is problematic.  I thought it was a Thunderbird problem, so I configured Evolution and attempted to send from that, but again, I received email but couldn't send.  I went back to Thunderbird, plugged an ethernet cable into my laptop and router, and was able to send my email.  So it looks like it's a wireless issue.
..........

Yep, a wireless problem of actually using someone else's unprotected wireless connection that allows you to access your POP server, but rejects your SMTP server settings because you are using a different ISP.

You may well be  having issues when someone else close by powers up their wireless network during the day, and your system connects to it.

---

### Post by Speedoo on 2008-01-16
Wow, interesting theory.  I hadn't considered that.  iwconfig shows that I'm connected to my own (unsecured) wireless network.  I do see another network in the area but it's encrypted.  OTOH, I probably should have mentioned that I receive email through my own domain hosted by Gate.com, but I send outgoing email (or try to!) through Comcast because I kept getting labelled as a spammer when I sent from my domain (apparently a Gate.com problem.)
Thanks for bringing another angle to my deductive reasoning!

---

