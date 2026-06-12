---
title: "Desktop configuration woes"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by mikemargle on 2007-04-25
I'm new to Ubuntu and chose Ubuntu over other Linux distos because of it's renowned community and ease of use.  I have a few problems setting up my desktop the way I would like.
1.  Dual monitors (single or separate desktops).
2.  Missing task? bars.  I'm missing the bars at the top and bottom of my desktop after editing xorg.conf to include my monitor's native resolution (1440x900).

Currently I have beryl running without problems on one monitor at 1440x900 resolution.  I have an NVIDIA 7900GT with the NVIDIA restricted drivers running.  I'm more concerned with getting my task bars back quickly.  However, I would like to get my dual monitors working as well.  I could never get them working properly in Edgy, and now that Feisty is here, I'm hoping I'll have better luck.  Thanks for your help!

Mike Margle

---

### Post by philbert on 2007-04-25
Hello Mike
I literally just finished my first Ubuntu install and I am using a Samsung 940MW which also has a native resolution of 1440 by 900 whereas on Fedora Core 6, I can get 1440 x 900. 
However on Feisty Fawn, I am able to get decent resolution at 1280 by 768. Sounds like it would not work since the ratio is 5 x 3 rather than 16 x 10 but it works best for me.
Hopefully I can figure out how to move to 1440 x 900 but this will work for me in the meantime.
Hope this helps
Phibert

---

### Post by mikemargle on 2007-04-25
I read elsewhere that in order to add a resolution to your available resolutions, you can go into your xorg.conf file and add the resolution at the front of each mode line, i.e. "1440x900" in front of the rest of the resolutions.  I'll see if I can't find that thread and post it here.  Hope this helps you.

update:
I reverted to my backup xorg.conf file, and for some reason the new resolution was there and defaulted, along with some other resolutions.  My task bars also came back to me!  Hooray Ubuntu and back-up files!

---

### Post by philbert on 2007-04-27
Hello Mike,
Putting 1440x900 at the beginning of those lines in xorg.conf worked. When I first opened the file I saw Feisty had already recognized the monitor but led with 1440x1440 and 1440x900 was not there.
Thanks for the tip.
Philbert

---

