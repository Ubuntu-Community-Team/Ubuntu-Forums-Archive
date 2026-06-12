---
title: "Canon MP160 64-bit drivers"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Mark C on 2007-05-22
Hi all.

I am currently using a 64-bit installation of Feisty Fawn, and I am wondering, where can I get a 64-bit version of the Canon Pixma MP160 drivers? I found an rpm of them at [http://www.canon-asia.com/](http://www.canon-asia.com/) but they are all 32 bit versions. 

I can also easily compile source files if there are any, but as I saw on the site, the source files are also 32-bit rpms, which gives an error when I 'alien' them to 64 bit.

Thanks for reading.

---

### Post by magicfab on 2007-05-23
The best place to ask that question would be Canon directly. Let them know you are using Ubuntu and you would require 64-bit drivers. Ask them nicely if they would be so kind as to provide Ubuntu packages on their site and perhaps even contribute them to the OpenPrinting.org project itself (if they' re not there already).

That being said, the drivers installed in any Gnu/Linux distribution (including Ubuntu) normally come from the Linux Foundation's Open Printing project. As such, openprinting.org always has the latest information / drivers for printer support.

This is the entry for your printer:
[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160)

---

### Post by Mark C on 2007-05-24
> **magicfab said:**
> The best place to ask that question would be Canon directly. Let them know you are using Ubuntu and you would require 64-bit drivers. Ask them nicely if they would be so kind as to provide Ubuntu packages on their site and perhaps even contribute them to the OpenPrinting.org project itself (if they' re not there already).

That being said, the drivers installed in any Gnu/Linux distribution (including Ubuntu) normally come from the Linux Foundation's Open Printing project. As such, openprinting.org always has the latest information / drivers for printer support.

This is the entry for your printer:
[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160)

Thanks for the info magicfab. That link was the one that had got me to the rpm site. Anyway, I already did a request to Canon's Singapore main site as you advised, now, I'm just waiting for their response :popcorn:. Thanks again.

---

### Post by hk_2999 on 2007-05-25
Never mind, I just installed the drivers on a chroot and used the 32-bit cupsd as my default printing daemon. It works flawlessly! :))

---

### Post by biodiesel-bri on 2008-01-20
Sweet!  Can you explain the process?

---

