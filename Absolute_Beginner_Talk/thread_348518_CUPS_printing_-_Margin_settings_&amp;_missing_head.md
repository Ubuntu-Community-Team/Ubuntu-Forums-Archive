---
title: "CUPS printing - Margin settings &amp; missing header/footers."
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by emarkay on 2007-01-28
I have the CUPS/PSC-1350 driver, using "hpijs" and HPLIP 0.9.7.  I have confirmed that I am using "letter" size paper.

There is (apparently) no way to adjust the printer margins.  

For example, see the attached "Print Preview" screencap from my browser's  (SeaMonkey 1.1) email.  The headers and footers print where they show, even though in my browser, I have specified a 0.5 inch margin.  

Does anyone have a solution to this?  

Thanks.

---

### Post by mitch.c on 2007-01-28
Select File -> Print, and then click the Properties button. There you will find "Gap from edge of paper to margin". Set values there at least equal to your printer's non-printable margin area.

This works in Firefox, and should be the same in SeaMonkey.

---

### Post by emarkay on 2007-01-29
Well look at me - OOPS - yea forgot all about that one!  (I reinstalled browser recently)

THANKS!!!

---

### Post by stuartk on 2007-04-05
I was just bitten by this one too. Ubuntu 6.10 with an  HP LJ 4200.

There are 2 places to set the margin in Firefox, properties from the print dialog, and then the other at File -> Page Setup.

The one in the print dialog properties was set to 0.04" and you can't set it any higher than 0.5" for some reason. Setting this to 0.5" all around helped, but not enough, so I also changed the top and bottom margins at File -> Page Setup to 0.7".

That did the trick.

---

