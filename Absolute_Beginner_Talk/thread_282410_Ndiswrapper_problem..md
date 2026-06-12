---
title: "Ndiswrapper problem."
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2006-10-22
Ok, I've got as far as modprobing ndiswrapper, when I type the command 'sudo modprobe ndiswrapper' I get this error. 

> FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/ndiswrapper/ndiswrapper.ko): Invalid arguement

What am I doing wrong?

---

### Post by Marsolin on 2006-10-22
I haven't used [NdisWrapper]("http://linuxappfinder.com/package/ndiswrapper") myself, but Tux Magazine has an [article]("http://www.tuxmagazine.com/node/1000167") on it. They did some configuration prior to running modprobe.

---

### Post by LukeyMI on 2006-10-22
See here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ#When_I_run_.27modprobe_ndiswrapper.27.2C_I_get_.27Invalid_module_format.27_or_.27Invalid_argument.27_error_or_something_similar._What_do_I_do.3F](http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ#When_I_run_.27modprobe_ndiswrapper.27.2C_I_get_.27Invalid_module_format.27_or_.27Invalid_argument.27_error_or_something_similar._What_do_I_do.3F)

---

### Post by Tux Aubrey on 2006-10-22
I has similar issues with command line ndiswrapper.  I downloaded the GUI utility via synaptic and everything worked just fine.  Just remember to copy the relevant driver folder from the CD to your machine before pointing ndiswrapper to the .inf file.

---

