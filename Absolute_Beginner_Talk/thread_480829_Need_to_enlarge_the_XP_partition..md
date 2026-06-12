---
title: "Need to enlarge the XP partition."
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by henthorn on 2007-06-21
I downloaded and burned the gparted disc but have no idea how to make it work.  All I get is the disc directory.

---

### Post by Clay_Banger on 2007-06-21
if you did everything correctly, put the cd in the computer and restart, it should boot up off the cd and load gparted, if it doesnt you may need to change the bios settings to allow it to boot off cd.

---

### Post by henthorn on 2007-06-21
Thanks, Clay.  That helped me get the disc to open, but I am still at a loss as to what choice to make among the options to get me to the place where I can resize the XP partition.

---

### Post by Clay_Banger on 2007-06-21
the default option is what u need. so at the menu just press enter.

---

### Post by santy_kushwaha on 2007-06-21
if u try to expand the xp partition then i will suggest use magic parition it is a good piece of software in doing these kind of job

---

### Post by Drakkor on 2007-06-21
sorry,think it's partition magic, so as not to confuse :o

---

### Post by henthorn on 2007-06-21
Thanks, Santy, but I have Partition Magic version 8.  I tried using it in XP but it is too old to be supported by XP and I no longer have the key that will allow me to download updates.  I don't do business with outfits that leave me out in the cold.  Got no help from Ipswitch(or whatever). I have gparted which should do the job but I think it was invented by a committee and I can't' figure out how to use it.  Of course I'm not too bright. I haven't tried it in Ubuntu, but I would be surprised if it worked there.

---

### Post by Drakkor on 2007-06-21
Try the GParted boot disk ? It's a partition editior, and can resize partitions.

---

### Post by Tyke91 on 2007-06-21
make sure you downloaded the ISO image, burn that to a cd, boot the cd just like you booted ubuntu.


then just hit enter for all defaults and you should be good.

---

### Post by henthorn on 2007-06-22
Tyjke91, I tried that.  Got through the language choice and quite a bit of stuff I didn't understand and then I got a message from the monitor diagnostic screen saying "unsupported mode" and nothing else happened.

---

### Post by Clay_Banger on 2007-06-24
> **henthorn said:**
> Tyjke91, I tried that.  Got through the language choice and quite a bit of stuff I didn't understand and then I got a message from the monitor diagnostic screen saying "unsupported mode" and nothing else happened.
ok, instead of hitting enter at the first menu, there should be an option in the list that says something like, "graphics safe mode" or "vga mode", try loading it with that one.

---

### Post by henthorn on 2007-06-24
Thanks, Clay.  Before I tried waha you suggested another lady said the same thing had happened to her with the latest gparted disc.  She went back to her old June 2006 2,5,2 version and it went right through.  I downloaded and burned the same version and it worked ok for me too.  Must be a bug in the newer version.  Any way I found that I couldn't do what I wanted to do.  When I installed Ubuntu to doublle boot I gave XP 10gb.  That was not enough so I thought that gparted would allow me to significantly enlarge the XP partition without harming my XP files.  Turns out gparted can't enlarge that partition by any significant amount.  It seems gpatrted isn't the great do-it-all that the Linux folks claim it is.  Thanks for your help.

---

### Post by Clay_Banger on 2007-06-24
> **henthorn said:**
> Thanks, Clay.  Before I tried waha you suggested another lady said the same thing had happened to her with the latest gparted disc.  She went back to her old June 2006 2,5,2 version and it went right through.  I downloaded and burned the same version and it worked ok for me too.  Must be a bug in the newer version.  Any way I found that I couldn't do what I wanted to do.  When I installed Ubuntu to doublle boot I gave XP 10gb.  That was not enough so I thought that gparted would allow me to significantly enlarge the XP partition without harming my XP files.  Turns out gparted can't enlarge that partition by any significant amount.  It seems gpatrted isn't the great do-it-all that the Linux folks claim it is.  Thanks for your help.

ah! with moving back to the old version you removed what you wanted to do, in a way.

you see, only the most recent gparted can resize/move/create ntfs partitions, but you couldnt boot into it, so you used an older version which doesnt have ntfs support, hence you were not able to do what you wanted to do. gparted will do what you want, its just you cant boot the new version. maybe you could try an older but still new version? if you get what i mean.

---

### Post by henthorn on 2007-06-24
Aha! Then Gparted is perhaps as good as they claim.  I will try a newer/older version and see if that solves my problem.  Thanks much, Clay.

---

### Post by Tripletaco on 2008-04-04
Gparted didn't work for me either.  I used 0.3.4-7 version which didn't work.  Then I tried the one that came with Gutsy.  It didn't work either.  I was able to shrink my Linux partition with the 0.3.4-7 version.   I made an unallocated spot right after my XP NTFS partion.  but it doesn't allow me to expand into it.

---

### Post by Daveg4otu on 2008-04-04
Try the Ultiimate Boot CD - contains several Partition managing applications -one of them should suit you.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by anjilslaire on 2008-04-04
Interesting. I use a GParted live cd to shrink my NTFS partitions and expand my /home ext3 partition just fine. Took forever, but it works.
I have a burned disc ver 0.3.4.8

When it boots, it craps out auto-detecting the vide resoluition, but I take th option to specify resolution ( cant recall th exact text) and it loads fine

---

