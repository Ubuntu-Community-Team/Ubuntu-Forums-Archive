---
title: "autodetect new moniter"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by nonewmsgs on 2007-05-13
i bought a new lcd moniter a mag innovision 22" wide screen.  it's a LT2219WDB.  i cannot find the refresh rates anywhere to adjust the xorg.conf myself, and since it's plug and pray it seems like it does not want to bother listing horizontal and vertical refresh rates anywhere (the lovely manual listed what parts it comes with in 5 languages but does not list anything useful).  how can i make ubuntu probe the moniter for the refresh rates?

---

### Post by heimo on 2007-05-13
Does this look like the same monitor?
[http://www.maginnovision.com/product/products-lcd-LT-2219wdb.htm](http://www.maginnovision.com/product/products-lcd-LT-2219wdb.htm)

---

### Post by Acksys on 2007-05-13
```
sudo dpkg-reconfigure xserver-xorg
```

helped me to autodetect some resolutions/refresh rates.

But a lot of LCDs are set at a refresh rate that you're not intended to change (60 Hz is the only one my laptop is supposed to use). Are you sure this isn't the case with your display?

---

### Post by nonewmsgs on 2007-05-13
heimo: YES! thank you! that's it.
Acksys: thank you too mate.  my main concern was actually just making sure i didnt fry it though...linux used to be infamous for that.

---

### Post by heimo on 2007-05-13
> **nonewmsgs said:**
> heimo: YES! thank you! that's it.

Ok, great. Then, just for the record in case the page disappears and someone else is looking for this information, I'll copy paste most relevant parts here:


```

Monitor                                      MAG innovision 22" wide screen LT2219WDB
Display Area                                 473.8mm x 296.1mm (18.7" x 11.7") 
Max. Resolution                              1680 x 1050
Horizontal Freq.                             30~ 82 KHz
Vertical Freq.                               56~ 76 Hz
Bandwidth (MHz)                              146 MHz
```

---

