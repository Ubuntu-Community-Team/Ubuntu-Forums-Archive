---
title: "printer images dithering"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by bobplano on 2007-05-07
after using ubuntu/linux for about a month now, i'm finally starting to get it to run exactly how i want it, except for this. i've attached pictures of it and the first one is the original picture(the printing press one) and the second  is the printed one (the otherimage file). it was scanned in so the quality isn't as good as the printed copy (another thing i need to work out), but the dithering is still there. i'm sure its a simple changing of printer options, but i don't know which ones to change to how much.

---

### Post by jiminycricket on 2007-05-07
What printer do you have?

Check out [http://www.linuxprinting.org/](http://www.linuxprinting.org/) for the specific model of your printer

---

### Post by bobplano on 2007-05-07
thanks for the link. i was just using the default drivers. i'll try gutenprint now and see how that works

---

### Post by bobplano on 2007-05-07
hmm once i installed gutenprint (both the rpm and the source ones) neither had the drivers for hp2000c. seems like this problem might not be as simple as i first thought

---

### Post by jiminycricket on 2007-05-07
That's odd, I guess you looked at [this]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-2000C") which said to use gutenprint for advanced features.  Still it's even odder that dithering appears on all pictures so even that shouldn't happen with hpijs.

Have you tried their mailing lists, at [http://lists.sourceforge.net/mailman/listinfo/hplip-help](http://lists.sourceforge.net/mailman/listinfo/hplip-help) and [https://lists.sourceforge.net/lists/listinfo/gimp-print-devel](https://lists.sourceforge.net/lists/listinfo/gimp-print-devel)

---

### Post by bobplano on 2007-05-07
well i'm using pcl3 because the hpijis drivers won't print for me. it makes some printery sounds for a minute then just stops, but it is still primed to print, even though it doesn't

---

### Post by bobplano on 2007-05-08
anyone know how to get the hpijis drivers to work or get some other drivers? i have ndiswrapper so i could use the drivers from hp but i don't know what else i need to make those work.

---

### Post by bobplano on 2007-05-11
it seems the only real problem is that gradients don't come out right with everything else being dithered but not too noticeably. is there a way to fix the gradients?

---

### Post by bobplano on 2007-05-12
since this seems to be a slightly more complicated problem than i thought, if no one here can answer this, can someone please move this to the printer support forum?

---

