---
title: "hard drive install"
date: 2007-07-24
forum: Apple Intel Users
---

### Post by andrewbossie on 2007-07-24
recently i put ubuntu as my only os on my mac book, my dvd drive has given out, (which im attempting to fix). now im wanting to dual-boot os x and ubuntu. i have made an iso of the install disk on another computer and transferred it via usb external HD. is there a way that i can make a hard-drive based installer to install os x? kind of complicated, i know!

-thanks!!

---

### Post by ivesjd on 2007-07-24
What you could try, is install to an external harddrive, and then copy that partition over to the laptop. Although you would need another mac for that.

---

### Post by cyberdork33 on 2007-07-25
> **ivesjd said:**
> What you could try, is install to an external harddrive, and then copy that partition over to the laptop. Although you would need another mac for that.

yep... you can actually use dd to clone the install image onto a bootable drive. I have done this with an iPod before actually. 

What would actually be easiest is you bring your mac to the other, hook it via firewire and turn on the mac with the broken Drive, booting into 'Target' mode (hold T during startup). This makes the 'target mode' mac appear to be an attached firewire drive, and you can then boot the install dvd in the other mac and install to the "firewire" drive.

---

### Post by ivesjd on 2007-07-25
> **cyberdork33 said:**
> yep... you can actually use dd to clone the install image onto a bootable drive. I have done this with an iPod before actually. 

What would actually be easiest is you bring your mac to the other, hook it via firewire and turn on the mac with the broken Drive, booting into 'Target' mode (hold T during startup). This makes the 'target mode' mac appear to be an attached firewire drive, and you can then boot the install dvd in the other mac and install to the "firewire" drive.

Those are both good ideas. And the first one I think could be done on any computer I would think. (although it would probably be tough on a windows machine).

---

