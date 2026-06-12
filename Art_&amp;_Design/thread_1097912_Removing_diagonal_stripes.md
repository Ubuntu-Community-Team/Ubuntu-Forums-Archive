---
title: "Removing diagonal stripes"
date: 2009-03-16
forum: Art &amp; Design
---

### Post by canoemoose on 2009-03-16
Hi all.

I've been playing around with the gtkrc for the Dust theme and I've managed to change the orangey browny colour of the loading bar and highlights etc to a slatey blue I like.  However, what bugs me now are the diagonal "hazard" stripes in the loading bar, which IMHO look tacky.  How do I disable them?

Cheers
canoemoose

---

### Post by Giant Speck on 2009-03-16
> **canoemoose said:**
> Hi all.

I've been playing around with the gtkrc for the Dust theme and I've managed to change the orangey browny colour of the loading bar and highlights etc to a slatey blue I like.  However, what bugs me now are the diagonal "hazard" stripes in the loading bar, which IMHO look tacky.  How do I disable them?

Cheers
canoemoose

The version of the Murrine engine in the repositories does not support progressbar options.

However, the newest SVN version of it (which can be found [here]("https://launchpad.net/%7Esuraia/+archive/ppa")), allows you to change the progressbar so that you can remove the stripes:

*progressbarstyle* = 0 

0 = nothing, 1 = striped, 2 = cells

---

### Post by canoemoose on 2009-03-17
Cheers!  I'll try it when I get a chance - I'm on my Windows box atm doing computing coursework.

EDIT:  Yep, this worked.  Cheers!

---

