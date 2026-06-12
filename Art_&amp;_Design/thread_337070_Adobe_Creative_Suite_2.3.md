---
title: "Adobe Creative Suite 2.3"
date: 2007-01-12
forum: Art &amp; Design
---

### Post by fiveryanfrenzy on 2007-01-12
I use Adobe Creative Suite 2.3 for Windows, can I make it work on Ubuntu?

its got illustrator, photoshop, indesign, golive, dreamweaver 8, acrobat pro and i think another one...

anyways should i just dual boot windows for using this huge suite?

---

### Post by hikaricore on 2007-01-12
_Free:_
You should probably check the wine application database for [individual adobe applications]("http://appdb.winehq.org/search.php?sSearchQuery=Adobe") to see what works and what doesn't.  I've had illustrator photoshop and acrobat working in linux myself with [wine]("http://wine.budgetdedicated.com/archive/index.html").

_Not Free:_
You may also have luck with [crossover]("http://www.codeweavers.com/products/cxoffice/") IF you desperately need a certain applications to work (I don't have time to check [their list of supported applications]("http://www.codeweavers.com/compatibility/browse/rank/?order=avg;sort=DESC") for you right now sorry) but as you can imagine this comes at a price.

---

### Post by Shay Stephens on 2007-01-12
> **fiveryanfrenzy said:**
> I use Adobe Creative Suite 2.3 for Windows, can I make it work on Ubuntu?


Easy answer, no.

Hard answer, you can get it to work in a virtual machine.

It doesn't work in wine.  It doesn't work in crossover office.

My advice, start thinking about converting your workflow to a different program(s) as the activation schemes will likely get worse as time goes by.  In the mean time, dual booting is the easiest solution.  Using a virtual machine is more convenient that dual booting.

I was using PSCS2 for editing raw files.  I have recently switched to using bibble.  I still use PS7 for text layout, that runs in wine .9.27 or crossover.  Wine .9.28 and .29 have busted Photoshop 7.  Hopefully .30 will fix that.  Until then, use .27

---

### Post by not_cool on 2007-01-13
[Here's]("http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/") a link on setting it up with wine, and it works, though I haven't tried it.

---

### Post by Shay Stephens on 2007-01-13
> **not_cool said:**
> [Here's]("http://blog.publicidadpixelada.com/2006/10/10/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/") a link on setting it up with wine, and it works, though I haven't tried it.

If you have not tried it, then how do you know it works?

---

### Post by stengah on 2007-01-28
Forget about wine .... use the free vmware server app to setup a virtual windows machine within linux and then install Adobe CS. It works wuperbly if you get the installation of vmware right. I've been using for 1year+ with no problems whatsover. You can then share files between the virtual machine and k/ubuntu by setting up samba.

There's a howto for setting up vmware server and windows somehere here on the forums. I have a link for it on my blog (see sig below) - Do a search for vmware and it oughtta pop up!

Cheers!

---

