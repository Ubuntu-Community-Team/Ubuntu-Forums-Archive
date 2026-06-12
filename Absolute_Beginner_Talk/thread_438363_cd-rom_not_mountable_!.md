---
title: "cd-rom not mountable !"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by thcman42069 on 2007-05-09
I am a new user to ubuntu, linux in general. I am enjoying everything about ubuntu, as it is completely better than windows. my only setback is that my cd-rom drive doesnt mount. when i go to "computer", and then doule click, or right clikand try to mount my "cd-rom 1" drive is states 

Unable to mount the selected volume.

show more details

mount: special device /dev/scd0 does not exist


any help ? i really depend on my cd- drive !

---

### Post by zvacet on 2007-05-09
**system>settings>removable drives&media**  find Cd and chek all boxes

---

### Post by Bachstelze on 2007-05-09
**/dev/scd0** ??? Where did you get that line from ? That's how BSD-based OSes label SCSI CDROM drives...

In Ubuntu, the disk should be mounted as soon as you put it in the drive. If you want to mount it manually, you'll have to find which device your drive uses. You can do that with for example :

```
dmesg | grep CD
```

---

### Post by thcman42069 on 2007-05-09
zvacet - all check boxes are enabled. still no success.

hymntolife - when i click "places" -> "computer" it opens the fiel browser and i double click "CD-ROM 1" and it gives me this 

Unable to mount the selected volume.

 i then click show more details and it givesme this line

mount: special device /dev/scd0 does not exist


i've googled for the whole day...around 8 hours....and still no success. i DO have a data cd in my drive...and i dont kno what im doing wrong !!! please help !

*** o , and for that line u gave me, hymntolife, i type it in terminal and there is no response.***

---

### Post by merlinus on 2007-05-09
Do you perchance have both a player and burner?  I do, and Ubuntu does not find nor load my burner.  I get the same error message as you, and no amount of asking for assistance on this forum and other places has resolved the problem.

I have to boot into Windows in order to burn cds.  Yuck!

-merlin

---

### Post by thcman42069 on 2007-05-09
yeah, its a cd-rw drive. i have to burn cd's from my laptop....still using ubuntu but everything is supported. im thankful for having two computers, cause if i didnt, i would be in a world of hurt right now. cause not only can i not burn cd's , i cant even load data off them.  <(^^,)>

---

### Post by eddieb on 2007-05-10
I have found the same prob. To get around it I inserted the blank disc and rebooted . The Places-Computer then showed Cdrom 1 and a Cd-rw 2. I was then able to burn to my hearts content!

---

### Post by thcman42069 on 2007-05-10
eddieb - thats what i found out yesterday. totally weird. but it worked !

---

### Post by kittyhawk63 on 2007-05-10
I'm using Gnome, not KDE.

I found that by first using Nautilus (Home) to locate my CD-R/W drive (have a data disk installed - **after** - you start Home, I was able to get it to mount. I left Nautilus (Home) open.
I then started k3b and I was able to burn an image.

---

