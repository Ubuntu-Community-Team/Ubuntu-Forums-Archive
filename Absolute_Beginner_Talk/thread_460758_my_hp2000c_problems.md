---
title: "my hp2000c problems"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by bobplano on 2007-06-01
I have spent sometime with linux, but one thing i have never been able to get working was my printer. my first problem was it wasn't detected. i did a combination of things, and it somehow got detected but i have no clue what i did to make it work. once i got it detected somehow, it wouldn't print pictures correctly. it dithered them, pretty badly too. i was using the pcl3 drivers because hpijis wasn't working. i found the hplip drivers but once i installed them and tried resetting up the printer it wasn't detected. I almost never boot into windows but when i need to print something i have to boot into windows. can anyone help me out here? i would appreciate any help

---

### Post by bobplano on 2007-06-02
bump

---

### Post by hummingbird59 on 2007-06-02
I assume that you have installed via the system/admin/printing/add printer route so if that failed to work for you, I would look at this page ([http://www.linuxprinting.org/show_printer.cgi?recnum=HP-2000C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-2000C)) and see if you might need to install a different driver.  As for printing photos, I have achieved fairly decent results with my HP Photosmart 230.  as for your particular printer and photos, I can't say.  Hope this helps!

---

### Post by bobplano on 2007-06-02
thanks for trying to help but i've already looked at that page and tried to install hplip. the problem is the printer isn't being detected now, despite me somehow getting it detected before and even with that i couldn't use the hpijis drivers, which probably would've made the pictures better. so now i'm just trying to get the printer redetected, because when i try to manually set it up, it doesn't work

---

### Post by bobplano on 2007-06-03
well out of curiosity, i put in the live cd and booted to it and checked to see if the printer was detected, and it was. does anyone know how to load the drivers so it can be detected without having to reinstall? i have gone through the software on the cd and i didn't see anything that seemed like it would help.

---

### Post by phidia on 2007-06-03
Just a guess but have you deleted the old printer and then selectedSystem>Administration>Printing to select a new printer?
You could also try to upgrade cups the printer software on your system.

---

### Post by bobplano on 2007-06-06
thanks, upgrading the software worked. its detected and now i can use the right drivers

---

### Post by bobplano on 2007-06-13
hmm. i just tried to reinstall the hplip drivers, and afterward, my printer wasn't detected anymore. now logic dictates then just don't use the hplip drivers, but the hpijis drivers aren't working any better than the pcl3 drivers. in fact, they're worse. so now i'm back to where i started basically, and again i need some help.

---

