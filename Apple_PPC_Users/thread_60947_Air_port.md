---
title: "Air port"
date: 2005-08-29
forum: Apple PPC Users
---

### Post by gumara on 2005-08-29
my ibook not found airport. how do

---

### Post by danns on 2005-08-29
You don't, there is no support for the Airport Extreme cards in Linux.

---

### Post by chascon on 2005-09-10
[QUOTE=]You don't, there is no support for the Airport Extreme cards in Linux.[/QUOTE]
Really?

See [http://forums.gentoo.org/viewtopic-t-365647.html](http://forums.gentoo.org/viewtopic-t-365647.html)

---

### Post by calum on 2005-09-11
[QUOTE=chascon]Really?

See [http://forums.gentoo.org/viewtopic-t-365647.html](http://forums.gentoo.org/viewtopic-t-365647.html)[/QUOTE]

Note that this requires patching Apple code, though, which may or may not be legal:
[URL=http://lists.terrasoftsolutions.com/pipermail/mol-general/2005-August/003848.html]http://lists.terrasoftsolutions.com/pipermail/mol-general/2005-August/003848.html
[/URL]

---

### Post by chascon on 2005-09-12
[QUOTE=calum]Note that this requires patching Apple code, though, which may or may not be legal:
[URL=http://lists.terrasoftsolutions.com/pipermail/mol-general/2005-August/003848.html]http://lists.terrasoftsolutions.com/pipermail/mol-general/2005-August/003848.html
[/URL][/QUOTE]
True, but so is running OS X via mol on non-apple ppc but people do it just the same.
I don't think this will discourage people from using it.  I for one hope that this will be refined considering that apple's choice to include a closed source wireless card in my laptop is an infringement of my digital freedoms.  As far as them finding out that one has altered 'their' driver, how do you suppose they are to do this?  Via spyware?  This would be a further infringement on our digital rights.  Besides, I don't believe airport extreme is not based GPL'd code anyway, despite propietary claims to the contrary.

Airport extreme itself presumably violates GPL on two counts.  First, it is based on Linksys WAP 54G (see below) which undoubtedly, in my humble opinion, is statically based on GPL code but its code is not fully released as required by GPL (violation #1).  Secondly, broadcom 43XX series cards, to which the airport extreme belongs to according to [http://linux-bcom4301.sourceforge.net/](http://linux-bcom4301.sourceforge.net/) (mailing list) allegedly violate airsnort by stealing their algorithm to create an anti-snort function (violation #2; see [http://lists.gpl-violations.org/pipermail/tech/2005-April/000025.html)](http://lists.gpl-violations.org/pipermail/tech/2005-April/000025.html)).  Thus, the restrictions to which you point seem frivilous.

"the broadcom chipset used by apple
for the airport extreme is also used in the Linksys WAP54G wifi access point
... which runs under linux. This of course means there is a kernel module that
drives the chip, and thus that either Linksys or Broadcom have code some
driver for it. It makes me angry to think they would have gone that far and
stopped there without considering their customers who care about running linux
on their apple hardware."
http://lists.debian.org/debian-powe...2/msg00445.html"

see also
[http://www.ussg.iu.edu/hypermail/linux/kernel/0309.3/0904.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0309.3/0904.html)

Of course, this assumes that the code has been kept from Linksys WAP 54G onwards to AE.  But even if it is not the same code but built based on it, it may still violate licenses as gnu-linux-ppc people incurr the same risk when they use darwin as base for gnu-linux-ppc.

---

