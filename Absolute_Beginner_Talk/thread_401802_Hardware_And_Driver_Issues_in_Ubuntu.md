---
title: "Hardware And Driver Issues in Ubuntu"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by riptreeper on 2007-04-05
I was running the live version of Ubuntu and I was wondering how I would get drivers for my wireless card and my display and whatever else needs a driver? Thanks in advance

---

### Post by irwa82 on 2007-04-05
Hi,

First question would be is there anything currently not working on your computer with the ubuntu live cd.

If everything works on the live cd then you will be all set after an install.

If something is not working on the live cd we are not mind readers and you will have to tell us what type of hardware it is that is not working so we can help with the drivers.

---

### Post by Famicommie on 2007-04-05
If your wireless card doesn't work out of the box, then you need to either check the manufacturer's website for linux drivers or you'll need to use a tool called ndiswrapper. Ndiswrapper is great; it allows you to use your Windows' wireless drivers. [More Info on Ndiswrapper here](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If you have an ATI card (I do), then you will probably prefer to use the proprietary ATI drivers over the open source drivers. I find significant performance increases by using the proprietary drivers. There is [a how-to available on how to do install those drivers here](https://help.ubuntu.com/community/BinaryDriverHowto/ATI).

I don't know anything about how the nVidia proprietary drivers work, but there is info on [how to install them here](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia).

Hopefully, your sound will work right out of the box.

Are you going to want multimedia codecs, too?

---

### Post by riptreeper on 2007-04-05
I may need the multimedia codecs. My sound does not work my video card kinda works but the display is weird so I'm leaning toward the not working correctly.  And my wireless card does not work. My mouse works but the special functions don't. I will take a look at the pages you provided but is there a way to use the .exe drivers that I have on my jump drive and would they work and can I install things like drivers in Live mode ? I also may need help on how to partition my hard drive so that I can run windows as a secondary os just in case thanks for the help

---

### Post by riptreeper on 2007-04-05
Oh and one more thing would windows games work in Ubuntu and if I could make them work how could I go about that

---

### Post by irwa82 on 2007-04-05
I have had a fair bit of success playing windows games with the transgaming cedega package.

check out [http://www.transgaming.com](http://www.transgaming.com) for details. 
also look at [http://transgaming.org/gamesdb/](http://transgaming.org/gamesdb/)

There is also quite a few good linux games but I assume you mean playing windows games you already have.

---

