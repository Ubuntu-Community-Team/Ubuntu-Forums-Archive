---
title: "Need Help Burning .dmg File on Ubuntu"
date: 2007-05-30
forum: Apple PPC Users
---

### Post by czechman86 on 2007-05-30
I am attempting to burn a .dmg file, so it is bootable when I restart my computer. However, I understand that .dmg is not burnable with Ubuntu. How can I burn it, so that it will boot properly, and also, are there any tools for maybe converting this .dmg image into an .iso. Thank you!

---

### Post by jamesjtucker on 2007-05-30
I found this thread in the forums which may help. 
[http://ubuntuforums.org/showthread.php?t=322042&highlight=convert+DMG](http://ubuntuforums.org/showthread.php?t=322042&highlight=convert+DMG)

It looks like you could mount the dmg, and then burn it that way.... If you have HFS support in your kernel, this should work:
[http://baghira.sourceforge.net/dmg.htm](http://baghira.sourceforge.net/dmg.htm)

Otherwise there are some good utilities to convert dmg to iso for windows, which could be run under wine.

---

### Post by czechman86 on 2007-05-30
@jamesjtucker

thanks man! the last tip would have worked great, but i downloaded a corrupt dmg. thanks for the tip, in the future, when i have a proper dmg, those will work great! :o

---

### Post by crypto2600 on 2007-11-23
Have you had a chance to check out AcetoneISO2?
[http://www.acetoneteam.org/central.html](http://www.acetoneteam.org/central.html)

It simplifies a lot of tasks relating to ISOs and other images.

---

### Post by bulletxt on 2007-11-25
yeah if you need to open a dmg file use latest AcetoneISO2 1.96 version. it will do the job for you.
of course you can allways use the terminal if you prefer ;)

---

