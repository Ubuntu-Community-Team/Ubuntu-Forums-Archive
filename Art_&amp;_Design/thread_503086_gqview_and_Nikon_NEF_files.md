---
title: "gqview and Nikon NEF files"
date: 2007-07-17
forum: Art &amp; Design
---

### Post by chichibabin on 2007-07-17
HI All,
I'm trying to get gqview to extract the full size jpeg which is embedded in all Nikon NEF files. On my Gentoo installation this was working with the latest build available for it (I'm sure it was but I could be wrong). Currently gqview-2.0.1-1ubuntu2 only extracts the crappy low res thumbnail jpeg from the NEF. I've seen there is a patch floating around for an older 1.5 version of gqview which allows viewing of the large jpeg. Was wondering if any had this working with a newer version of gqview under Ubuntu???
Cheers,
Sat

---

### Post by chichibabin on 2007-07-19
I think the they may have added the full size jpeg support in the development version of gqview which is 2.1.5. Does anyone know where I can get a .deb package of this version?
Is it possible to get synaptic to display development versions as well and not just stable stuff?

EDIT: I'm rather new to this .deb business and figured out that I could use Alien to convert a readily available rpm to a deb of version 2.1.5. I installed it and the full size jpeg extraction works!
Cheers,
Sat

---

### Post by PoTs on 2007-10-19
These are the actions i performed:

download gwview rpm from sourceforge.net
in a command interface:
install alien with 'sudo apt-get install alien'
convert to deb with 'alien --to-deb <gqview rpm package name>'
install the package with 'dpkg -i <gqview deb package name>'
Then you can start gqview from the menu 'Applications/Graphics/gqview'

And it works.

---

