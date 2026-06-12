---
title: "Unable to Install Ubuntu 7.10"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by waffleboy on 2008-01-22
Yea, im new at ubuntu and linux in general, so i tried to install Ubuntu 7.1. i dl and burn it successfully using ultra iso, and i put it into my drive, i boot up into the gfx screen, i hit enter at the start/install ubuntu option, then it says its loading, then i get the Ubuntu gfx loading screen. that loads and i end up with some busybox error, and a prompt starting with (initramfs) i have no idea wat happened, ive tried multiple solutuons but none have worked, if someone can help me fix this id greatly appreciate it.

---

### Post by philinux on 2008-01-22
Good idea to post system specs including graphics card.

You might need the alternate text based installer if the graphics card is the problem.

---

### Post by waffleboy on 2008-01-22
Ive got 
Celeron D 360 3.46 ghz processor
2 gb ram
8600 GTS 
120 gb Sata 

i dont think its the gfx card because this whole setup is brand new, and i just got the gfx card month ago

---

### Post by philinux on 2008-01-22
when I say graphics card problem I mean it might not be supported by ubuntu.

The alternate text based install doesn't need to recognise the gfx card. Then after install you can sort out the graphics card properly.

---

### Post by waffleboy on 2008-01-22
O ok, how might i do that? i dont know alot about ubuntu, but i do know some coding so im not oblivious

---

### Post by philinux on 2008-01-22
If you search these forums for 8600 gts a few peeps have had problems. Anyway see the screenshot. Just below START DOWNLOAD is a check box for the alternate cd.

Another thing to check is the option on the live cd to check the cd for errors. I would do this first.

---

### Post by waffleboy on 2008-01-22
ok thanks


im gonna try the cd check and get back to you


Edit: When i run the cd check it still gets the error with busybox shell (ash) with the (initramfs) prompt

---

### Post by jken146 on 2008-01-22
Try the alternate CD.

---

### Post by waffleboy on 2008-01-22
Im im dling the altenate text based cd, wat do i hav to do to make this work?

---

### Post by travis31 on 2008-01-22
> **waffleboy said:**
> ok thanks


im gonna try the cd check and get back to you


Edit: When i run the cd check it still gets the error with busybox shell (ash) with the (initramfs) prompt

I had the same problem when trying to install on my laptop. As suggested above, try the alternate text based installer. I accepted most of the defaults for the X configuration and the graphics worked fine. I guess the live cd based installer is not fully compatible with newer hardware.

---

### Post by waffleboy on 2008-01-22
Yea i guess, kinda annoying

---

### Post by waffleboy on 2008-01-22
i attempted to install ubuntu, i got to the text based installer, but then i got messed up @ the partition part, i already had a pre-partitioned external hd i was gonna boot it off of, and i didnt want to format the whole thing. i deleted the partiton now, will ubuntu auto partition the external w/o formatiing so i can install saving my data?

---

