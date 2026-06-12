---
title: "Can't install inkscape :("
date: 2009-03-13
forum: Art &amp; Design
---

### Post by matty-guy on 2009-03-13
I downloaded inkscape, unpacked it all, and ran ./configure, and when it is about to finish it says: "configure: error: libpng >= 1.2 is needed to compile inkscape"
I then went on to install the latest libpng, and it still wouldn't install. I placed the files in the same directory, it still wouldn't install.
Anyone had this problem? Please help.
Couldn't decide which forum this would go in so i decided, it being a graphics program, it would go in design :)


EDIT: Nevermind, im using linux mint (ubuntu variant) and i went to mint install and it allows me to install it via that so it doesnt matter now.

---

### Post by renzokuken on 2009-03-13
Inkscape should be in the repos. unless you need the bleeding edge release i recommend installing from the repos as follows. (incidentally, this will also automatically take care of any dependencies e.g. libpng)

Open up Synaptic Package Manager (System -> Admin -> Synaptic) then search for and install inkscape.

alternatively you can do it from the command line using

```
sudo apt-get install inkscape
```

EDIT, just noticed you edit so congrats on figuring it out yourself. but my advice is always check to see if a program is in the repos before trying to compile anything

---

