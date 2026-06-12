---
title: "Loading Live CD - Errors/Blank Screen"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by P3RH4PS on 2007-09-14
Using the Kunbuntu AMD64 live cd I click install and it all looks good then text starts scrolling some looks fine [ OK ] then others say "error loading somethingorother" then after some more errors and oks my lappy lets out a "Beep!" and more loading happens for like 4 seconds then "BAM!" blank screen, cd stops reading, just chillin'.  I ran the scan thing that checks the cd for errors and it came back ok.  Computer crashed on the memcheck thing but I was out of the room when it happened so I'm  not sure why.  Safe graphics mode does the same thing.  CTRL+ ALT +F1 does: NOTHING!  :guitar:

I'm not sure whats wrong with lappy! Help!

AMD Turion64x2 - 1.83Ghz
2gigs of RAM
GeForce Go 6150 - Integrated 271MB Dedicated 64MB - Total 335MB
Has currently Windows Vista - Professionaly Sux Edition 32bit Brought to you by HP

HP Pavillion dv6000

Thanks for helping!

---

### Post by aspen_dv on 2007-09-15
Sounds like memory problem. Can you try to remove half of your memory and see if it makes any different? If it crash, then try with another half, see if you can isolate the bad memory.

---

### Post by alienexplorers on 2007-09-15
try running:
> sudo dpkg-configure xserver-xorg

---

### Post by P3RH4PS on 2007-09-15
When/where/how would I run

sudo dpkg-configure xserver-xorg

(Sorry I'm a complete nub)

---

### Post by Maestro23 on 2007-09-15
> **P3RH4PS said:**
> Using the Kunbuntu AMD64 live cd I click install and it all looks good then text starts scrolling some looks fine [ OK ] then others say "error loading somethingorother" then after some more errors and oks my lappy lets out a "Beep!" and more loading happens for like 4 seconds then "BAM!" blank screen, cd stops reading, just chillin'.  I ran the scan thing that checks the cd for errors and it came back ok.  Computer crashed on the memcheck thing but I was out of the room when it happened so I'm  not sure why.  Safe graphics mode does the same thing.  CTRL+ ALT +F1 does: NOTHING!  :guitar:

I'm not sure whats wrong with lappy! Help!

AMD Turion64x2 - 1.83Ghz
2gigs of RAM
GeForce Go 6150 - Integrated 271MB Dedicated 64MB - Total 335MB
Has currently Windows Vista - Professionaly Sux Edition 32bit Brought to you by HP

HP Pavillion dv6000

Thanks for helping!

Found some threads that might help:

HP DV6000 Success: [http://ubuntuforums.org/showthread.php?t=460553&highlight=HP+Pavillion+dv6000](http://ubuntuforums.org/showthread.php?t=460553&highlight=HP+Pavillion+dv6000)

HP DV6000 Wiki Page: [https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))

Good luck man. :)

---

