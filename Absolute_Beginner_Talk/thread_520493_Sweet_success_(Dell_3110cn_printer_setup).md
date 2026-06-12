---
title: "Sweet success (Dell 3110cn printer setup)"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by lost4now on 2007-08-08
Here is my story....

For several months I have been trying to configure a Dell 3110cn color laser print to work in UBUNTU. A lot of reading then a lot of forum questions. Not many answers.

Nothing seemed to work and I was ready to sell a very near new printer for little or nothing just to get rid of it. 

This is how I finally got things working.

1. select system --> administration --> printing

2. Right click on new printer --> select add new printer --> click on Network printer --> select HP jetdirect. (this is no mistake. Just do it)

3. fill in the host with "http://localhost:631". Leave the port at 9100.

4. Select "generic" for a manufacturer then "PostScript Printer" for a model.

5. Next put whatever you want for Description and Location.

6. close out and when your printer shows up in the printers window highlight it and right click. Select properties.

7. This is where you will think I'm nuts but it works. Open firefox or whatever browser you use. Enter "http://localhost:631/" on the command line and enter it. You should now be in the CUPS setup window. 

8. Near the top of the page select "Printers". A page should come up showing all the printers you have set up in the printers page. Select "Set Printer Options". Make any changes for the printer you just set up and select the "Set Printer Options" green button to save them.

9. Close out of everything and enjoy. :)

I am sure there are a dozen other ways to do this but it took me a few dozen try's and a few weeks of frustration to figure this thing out but it worked for me. I don't want to hear about what I did wrong. IT WORKED. End of story. I just hope it will save some time and effort for someone else.

This also solves the problem of the printer trying to print A4 paper size also.

---

### Post by jnorthr on 2007-08-08
Congrats :) This is how we all learn a little bit about solving problems. Does your printer do both sides of the paper ? 

The CUPS service is one choice  for spooling support, i think there is also an HPLIX (or similar) service for HP devices, but not having one, i cannot try it out.

---

### Post by lost4now on 2007-08-08
I  have the duplexer option so it does both sides.

---

### Post by mar225 on 2007-08-08
Solved my problem.  Three thumbs up for you.

---

### Post by univremonster on 2007-08-08
Awesome!  Now maybe you can help me with my Lexmark....

---

### Post by lost4now on 2007-08-08
Go for it univ. I'll do what I can.

I think Dell printers are made by Lexmark so it shouldn't be that much different.

---

### Post by philinux on 2007-08-08
Thanks for this - [http://localhost:631/](http://localhost:631/) - never new it existed or where to find it. anyway my epson shows up and I can do head cleaning etc. 

Is this url documented or have I just missed it.

---

### Post by bwtranch on 2007-08-08
I had a similar deal with my Brother DCP 1000 and I finally solved that:lolflag:
After the party was over I posted the fix on this forum. It was even weirder than yours because it messes up dpkg and you have to know how to fix that or you can't install anything else.
If anybody is interested they can look that up. Cheers:)

---

### Post by lost4now on 2007-08-08
Philinux,

I think the localhost thing is part of the standard setup from cups but by the time I got to it I was so confused I was lost. I think my path to it works easier. At least it did for me.

---

### Post by jnorthr on 2007-08-08
see [http://home.swbell.net/berzerke/printing.html](http://home.swbell.net/berzerke/printing.html) for an explanation

---

### Post by univremonster on 2007-08-14
> **lost4now said:**
> Go for it univ. I'll do what I can.

I think Dell printers are made by Lexmark so it shouldn't be that much different.

Lexmark X5270, used to run it on a Windows laptop, now I have the following hardware:

 	 Seagate Barracuda 7200.9 ST3250824AS 250GB 7200 RPM SATA 3.0Gb/s Hard Drive
         AMD Athlon 64 3400+ Venice 2.2GHz Socket 939 Processor Model ADA3400DAA4BY
 	 SAPPHIRE PC-A9RD480Adv Socket 939 ATI Radeon Xpress 200 CrossFire ATX AMD CrossFire Motherboard
 	 Patriot 1GB 184-Pin DDR SDRAM DDR 400 (PC 3200) Desktop Memory Model PSD1G400

---

### Post by jroper on 2008-05-18
Interesting... On Hardy, to print to a Dell 3110cn on my local network, I just created a new LPD/LPR printer, entered the host name, and selected a Generic Postscript printer.  It just worked.

---

