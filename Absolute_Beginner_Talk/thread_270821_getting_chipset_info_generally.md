---
title: "getting chipset info generally"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-10-03
Hey all. I'm having issues with my graphics driver, and earlier I had trouble setting up my modem. Solving both did/will involve getting my chipset info. I now know about scanModem, but how do I get my graphics card info? For future reference, how do I get info on any and all of my chipsets? Is there one data file somewhere on my system for this? Alternately, is there one terminal command that will give me what I need. I know about lspci, but when I seek help with what I get here, I'm regularly told this is not enough. TIA.

---

### Post by po0f on 2006-10-03
ricardisimo,

Try running lspci with the -v option, for verbose.  It will print out a lot more information.

---

### Post by llamakc on 2006-10-03
sudo lshw

---

