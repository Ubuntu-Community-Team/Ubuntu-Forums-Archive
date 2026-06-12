---
title: "To die trying ati drivers i need to know if this is right!"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by idecrash on 2007-06-22
how to enable using :kdesu kate /etc/default/linux-restricted-modules-common,
this is what i have:
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""

how do I enable fglrx? plz help me!
i almost had it the last time( aticonfig messed it all up, I had 2 desktops imbedded into 1 another, I need to know what to do to edit in kate to enable fglrx.

---

### Post by idecrash on 2007-06-22
how do I enable fglrx w/ kate? please anyone can you help me?

---

### Post by NeoLithium on 2007-06-22
This guide [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)  should be what you're looking for, to get the ATI drivers up and running.

---

### Post by idecrash on 2007-06-22
Hey thanks man I want to say bam! full 3-d but i guess i have to wait for ATI to give out the code until then i can deal w/ it. but would really like to thank you for the info/help, i do have drivers loaded and ati catylist control center can do very little but its worth it to speed up the card from standard drivers, maybe ATI`s next release will let me enable full acceleration and 3-d, for this radeon x1650pro 512mb, card. just wish they would hurry up.

---

