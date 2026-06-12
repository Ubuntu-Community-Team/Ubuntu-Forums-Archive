---
title: "[SOLVED] ATI 3D Rage II+ [Mach64 GTB] All In Wonder"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-09-22
I've tried some of the things mentioned on other posts and haven't had any luck getting this card to work in Ubuntu 7.04.  It is an older PCI ATI All In Wonder card.  Following the suggestions on one of the posts, here is some information:

lspci -n | grep 0300  shows:

00:0d.0 0300:  1002:4775 (rev 9a)

 lspci | grep VGA  shows:

00:0d.0 VGA compatible controller: ATI Technologies Inc  3D Rage II+ 215GTB [Mach64 GTB} (rev 9a)


If someone could help me get this card working it would be greatly appreciated!!:)

Thanks in advance!

---

### Post by alienexplorers on 2007-09-22
Mis-read the card type I thought it was a Radeon AIW.  You might be able to get it running with the ATI driver.  Run dpkg-reconfigure xserver-xorg and select the ati driver.

---

### Post by anewguy on 2007-09-24
BTW - not knowing what the heck some things are, I have already tried the sticky for ATI "X" cards.  It screws up my xorg.conf so much that x won't start.  Can't get it to work just using the generic "vesa" driver either.

Anyone got any ideas, or should I just give up on this video card?

Thanks!:)

---

### Post by overdrank on 2007-09-24
> **anewguy said:**
> BTW - not knowing what the heck some things are, I have already tried the sticky for ATI "X" cards.  It screws up my xorg.conf so much that x won't start.  Can't get it to work just using the generic "vesa" driver either.

Anyone got any ideas, or should I just give up on this video card?

Thanks!:)

I had a similar card in a laptop about the first of the year and I used envy and that gave me the best graphics. I don't know if envy will still support that old of a card, :(

---

### Post by anewguy on 2007-10-21
No, envy didn't work either.  I suspect I just need to get rid of the card and get something a little more current.:)  So, I'll be marking this closed.

---

