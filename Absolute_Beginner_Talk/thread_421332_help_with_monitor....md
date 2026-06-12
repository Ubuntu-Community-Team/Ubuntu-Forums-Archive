---
title: "help with monitor..."
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-04-24
when ever i use a monitor or projector with my VGA output, it crashes the whole system when i unplug it, and try to go back to origional resolution (1280 x 800). is there a program or driver that will control my monitor functions, and make my computer work with my VGA port?

---

### Post by dstew on 2007-04-24
What are your system specs? What is your video card and driver?

---

### Post by kevin11951 on 2007-04-24
> **dstew said:**
> What are your system specs? What is your video card and driver?

I'm using Ubuntu 7.04 feisty, laptop, and a 100% generic hardwired-to-circuit-board video card from dell (either Mobile "915GM/PM/GMS/910GML" or "Mobile 915GM/GMS/910GML Express Graphics Controller".

---

### Post by dstew on 2007-04-25
Have you installed the drivers for that card/chipset? It sounds like you are running a generic driver, so it behaves badly. [Here]("http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21") is a link to the Intel drivers page for Linux. I do not know if there is an easier way, but here they give source code that needs to be compiled. If you have not compiled from source before, it might be tricky.

---

