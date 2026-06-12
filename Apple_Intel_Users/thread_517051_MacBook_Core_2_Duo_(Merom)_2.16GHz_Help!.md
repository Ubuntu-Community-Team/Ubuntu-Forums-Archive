---
title: "MacBook Core 2 Duo (Merom) 2.16GHz Help!"
date: 2007-08-04
forum: Apple Intel Users
---

### Post by amk29j on 2007-08-04
Hey guys,

I am having trouble installing Ubuntu on my new MacBook.  I am not new to the Ubuntu world, I had it on my old Dell, but I have spent a couple of days trying to install this and I just can't get it to work!  

I have tried to follow this: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
The problem I have with this is > To prevent a kernel panic which might occasionally occur, press F6 and enter one of the following parameters at the boot: prompt:
lpj=8000000 (for 2 GHz MacBook) or lpj=7330000 (for 1.83 GHz MacBook)

I have neither the 2GHz or the 18.3GHz.  Might this be the problem?  I have tried other Howtos elsewhere.

This is what happens.  I load the CD, most of the time I don't have keyboard access, so if anyone knows a workaround to that, it would be greatly appreciated.  Then (when I happen to have keyboard access), I try to install it.  I have tried to change it so that it isn't VGA (Option F4) and I've also added lpj=8645184 to Option F6 (a number I randomly found associated with 2.16 GHz iMac).  But no matter what, the splash screen comes up for a couple of minutes, then a black screen with a cursor, and finally a bunch of errors about some sectors or something like that.

If anyone could please help it would be greatly appreciated.  I have tried to look through the forums and I could not find answers.

Thanks,
-Ahmed

---

### Post by cyberdork33 on 2007-08-04
you are gonna have to be more descriptive with the error message

---

### Post by Peavey on 2007-08-04
I too have a 2.16 GHz Core 2 duo, and while I am having issues getting it to work under Parallels, it has no issues whatsoever when I just boot straight from that partition.  I didn't even have to worry about the problem you mentioned with the 2.0 and 1.83 GHz machines.  I just installed it following the directions in the wiki, word for word with no lpj=**X**, and it worked fine.

Now, I too cannot use the native resolution of my MacBook, but I think if you reinstall and just leave the resolution at 1024*768 it should work.  I'm not going to worry about getting the right resolution until I can get it working through parallels.

---

### Post by amk29j on 2007-08-04
> **cyberdork33 said:**
> you are gonna have to be more descriptive with the error message

I will get you the real error messages tomorrow when I try again.

> I didn't even have to worry about the problem you mentioned with the 2.0 and 1.83 GHz machines. I just installed it following the directions in the wiki, word for word with no lpj=X, and it worked fine.

I am only assuming that this is the problem.  Sorry for not being clear.  Again, I will give you guys more information tomorrow.

Thanks for your prompt responses!

-Ahmed

---

### Post by cyberdork33 on 2007-08-04
> **Peavey said:**
> Now, I too cannot use the native resolution of my MacBook, but I think if you reinstall and just leave the resolution at 1024*768 it should work.  I'm not going to worry about getting the right resolution until I can get it working through parallels.


Parallels will use a different video driver, but natively you can install 915resolution.

---

### Post by amk29j on 2007-08-04
OK, this is what happens.

First after I press enter to Install the things, it says Starting.  Loading Linux Kernel.  It loads to 100% fine.  Then I get the splash screen which appears to be loading (and I hear the CD-ROM spinning).  Then I get a black screen with a cursor and I get the following error messages over and over again:

```
SQUASHFS error: sb_bread failed reading block 0x1d519
SQUASHFS error: Unable to read fragment block [7544c1b]
SQUASHFS error: Unable to read page, block 7544c1b size 1944
Buffer I/O error on device sr0, logical block 60976
```

Thanks for your help.

---

### Post by Loki1989 on 2007-08-05
thos instructions that you posted a link to got me installed very quickly all I need is my wireless for now to update everything else

---

### Post by amk29j on 2007-08-05
> **Loki1989 said:**
> thos instructions that you posted a link to got me installed very quickly all I need is my wireless for now to update everything else

Why am I getting these errors then?

---

### Post by Loki1989 on 2007-08-05
I do have a 2.16 Ghz model also and I used boot camp to partition and installed after that I am sorry that you are not having a good experience with Ubuntu on your mac.

---

### Post by ivesjd on 2007-08-05
Could it be a bad burn? Maybe trying burning Ubuntu again at a slower speed.

---

### Post by cyberdork33 on 2007-08-05
> **ivesjd said:**
> Could it be a bad burn? Maybe trying burning Ubuntu again at a slower speed.
yea it can't read the filesystem on the disk.

---

### Post by russo.mic on 2007-08-08
If it's a video problem, then you need to install FGLRX.  the 915resloution won't help, as you've probably got an ATI X1400 in that thing.  

So, if the error is about XServer starting, have a look at my post here:

[http://ubuntuforums.org/showthread.php?t=510390&](http://ubuntuforums.org/showthread.php?t=510390&)

That should get you going!

good luck.

Russo

---

### Post by cyberdork33 on 2007-08-08
> **russo.mic said:**
> If it's a video problem, then you need to install FGLRX.  the 915resloution won't help, as you've probably got an ATI X1400 in that thing.

MacBooks do not have ATI graphics, only Intel graphics. MacBook Pro has ATI graphics (well, now it is nvidia).

---

### Post by amk29j on 2007-08-08
Hey thanks for the replies.  I actually don't doubt that it's the CD, my last CD wouldn't even take me to the Loading... screen.  I think these CDs are defective.  I don't know when I'll be able to get more CDs.  Hopefully my sister has one that I can steal before I move back to school.  And, as a side note, I wish I wasn't working so much so I can do this!

Thanks again guys.
-Ahmed

---

### Post by cyberdork33 on 2007-08-08
> **amk29j said:**
> Hey thanks for the replies.  I actually don't doubt that it's the CD, my last CD wouldn't even take me to the Loading... screen.  I think these CDs are defective.  I don't know when I'll be able to get more CDs.  Hopefully my sister has one that I can steal before I move back to school.  And, as a side note, I wish I wasn't working so much so I can do this!

Thanks again guys.
-Ahmed

I often have issues with CDs burned on a Mac unless I burn them slowly. Try turning the burn speed down when writing the disc, and you may have more luck.

---

### Post by ivesjd on 2007-08-09
Thats why I liked my Lite-On drive. Burned Ubuntu iso's at 52x and they always worked. My hacked windows disc's on the other hand, would take 3 or 4 tries to get them write. :/

---

### Post by cyberdork33 on 2007-08-09
> **ivesjd said:**
> Thats why I liked my Lite-On drive. Burned Ubuntu iso's at 52x and they always worked. My hacked windows disc's on the other hand, would take 3 or 4 tries to get them write. :/

Oddly enough, the same images burned under Ubuntu usually work fine...

---

