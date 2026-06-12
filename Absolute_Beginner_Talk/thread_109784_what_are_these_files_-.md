---
title: "what are these files? -"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by ephman on 2005-12-29
hi,

what are these files for?  are they part of the restricted modules? 

root@wintermute:/lib/modules/2.6.12-10-686/volatile# ls
ath_hal.ko  fcdslsl.ko     fcdslusba.ko  fcpcmcia_cs.ko  fglrx.ko
fcdsl2.ko   fcdslslusb.ko  fcdslusb.ko   fcpcmcia.ko     fxusb.ko
fcdsl.ko    fcdslusb2.ko   fcpci.ko      fcusb.ko        nvidia.ko
root@wintermute:/lib/modules/2.6.12-10-686/volatile#

thanks,
ephman



edit: this sorry this

---

### Post by Lambert on 2005-12-29
I believe .ko files are kernel modules. 

for example the ath_hal.ko is a dependant module for the madwifi wireless driver module ath_pci

interesting that they fall under a volatile directory.

---

### Post by ephman on 2005-12-29
any idea why they've ended up there?  might be a clue as to why i'm having this webcam driver install issue.  

thanks, that's what i thought as well which is why i asked, it's strange.  i'm having a tough time figuring out a nw802 webcam driver issue.  where should these files actually then?  looks like the volatile directory, by the files listed is where dependant kernel modules are kept for restricted modules.  does that make sense?

thanks for the bandwidth,
ephman

---

### Post by Lambert on 2005-12-29
Not a whole lot of activity or documentation on this project. 

I would suggest trying their mailing list to see if anybody can help you.

[http://lists.sourceforge.net/lists/listinfo/nw802-main](http://lists.sourceforge.net/lists/listinfo/nw802-main)

---

### Post by ephman on 2005-12-29
thank you i feel as though i'm getting close to figuring this out.  as you said there's not much documentation and the group as well is pretty dead, not much action going on.  i've read through the complete thing over the past few days.

be well,
ephman

---

