---
title: "Burn Live CD in DSLinux"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by amazingtaters on 2008-03-21
Okay, so after some struggles with my video drivers, X had a catastrophic crash. I mean, it was just totally destroyed. So, I decided I'd whip out my XP disc, install XP, and download a live cd image then burn it off. Well, apparently my Laptop hates XP, and will not install it. It would be in the middle of installs and just crap out, lappy would turn off, and I'd be back to square one. Right now I've got DSL running, and I am wondering how I can burn the live cd for ubuntu with the default cd burning software in DSL. Thanks in advance for any help.

---

### Post by spiderbatdad on 2008-03-21
Here's an example. Obviously you would replace the filename.iso as appropriate.[http://damnsmalllinux.org/wiki/index.php/Burning_a_Bootable_CD](http://damnsmalllinux.org/wiki/index.php/Burning_a_Bootable_CD)

or you may be able to just proceed with the command:```
cdrecord dev=/dev/cdrom driveropts=burnfree -v -data cd_image.iso
```

where cd_image.iso is replaced by the actual filename. Note: you need to be in the same directory as the file. So, if it is on your desktop, first cd Desktop.

---

### Post by amazingtaters on 2008-03-21
Ah merci beaucoup.

---

