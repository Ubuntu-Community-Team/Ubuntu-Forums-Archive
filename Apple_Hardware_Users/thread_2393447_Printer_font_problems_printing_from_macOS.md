---
title: "Printer font problems printing from macOS"
date: 2018-06-03
forum: Apple Hardware Users
---

### Post by waltman on 2018-06-03
I'm having an odd printing problem since upgrading from 17.10 to 18.04. I've got an Ubuntu box that I've been using as a shared printer. I've also got a MacBook running the latest version of macOS, which is where most of my print jobs originate. The printer in question is an HP LaserJet P1006.

If I print from the Ubuntu box while the printer is plugged into it (it's USB-only), everything looks fine. Similarly, if I plug the printer into the Mac and print from there, it also looks fine. However, if the printer's plugged into the Ubuntu box and I print from the Mac, the fonts are all messed up. If I print, say, the Google home page, the images look fine, but the text areas render as a bunch of boxes and random characters.

I also tried printing a PDF that I created with LaTeX. Interestingly, that printed perfectly!

This same setup had been working fine up to 17.10, but failed the first time I tried to print after switching to 18.04.

I've tried reinstalling the drivers on both ends, but it didn't help.

I've looked at all the CUPS settings but I don't see anything that might be causing this behavior. Is anyone else having this problem?

---

### Post by wildmanne39 on 2018-06-03
*Thread moved to **Apple Hardware Users for a more appropriate fit**.*

---

### Post by waltman on 2018-06-03
I guess I see why you moved this post, but the fact that it happened after installing 18.04 -- without changing anything on my Mac -- makes me think this is an issue with Ubuntu, not the Mac.

---

### Post by donaldsbell on 2018-07-02
I am experiencing the same problem - I upgraded to 18.04 and now my Macs and iPad no longer print readable documents.  The characters are getting garbled and printed as blocks.

I also think it is a Ubuntu thing as three different Apple products stopped working.

---

### Post by wildmanne39 on 2018-07-02
Hello and welcome to the forum donaldsbell, please start your own thread so you can get the help you need instead of posting in someone else's.

Thanks

---

### Post by jwilentz on 2018-09-28
Having the same problems printing via Google Cloud Printer on my Mac through my Linux box connected to my printer after upgrading Ubuntu to Busy Beaver. Nothing has changed on the Mac and the printer is the same HP printer. System worked perfectly before upgrading Ubuntu to Busy Beaver so this is not a Mac or HP problem. What to do??

---

### Post by uhansen on 2018-10-05
I had the same problem, after updating my Ubuntu 16.04 LTS server (intel NUC5i5RYH) to 18.04 LTS on September 23rd, 2018. The server is connected via USB to a Brother HL-1430 laser printer. The printer is shared with CUPS over the network to two MacBooks, one running High Sierra, one with El Capitan.

Everything worked fine with 16.04 LTS. After updating to 18.04 LTS I get gibberish, garbage, garbled fonts, when printing from my Macs.

It is interesting though, that it worked OK when I printed documents directly from Word 365 on the Mac or from Photoshop Elements.

But everytime macOS uses the built-in "Preview" app, fonts become strange squares, lines and circles. "Preview" is used all the time, for instance when printing a mail attachment or a PDF so it is not possible to avoid it.

I tried several things to solve this problem:

I connected the printer directly to the Macs (works)
I print the PDF directly with "lp" from the Ubuntu server (works)
I purged and reinstalled CUPS on the server (didn't help)
I used different drivers (Gutenberg, brother-cups-wrapper-laser1, Turboprint) (didn't help)
I reinstalled the printer on my Macs several times. (didn't help)
I even used a second printer of the same make and model (didn't help)
Printing from an iPhone / iPad, which found the CUPS printer over Avahi/Airprint also resulted in a printout with the strange fonts.

In the end I deleted 18.04 and made a fresh install of the old Ubuntu 16.04 LTS. Everything works now. I hope someone cracks the problem eventually. Thanks!

---

