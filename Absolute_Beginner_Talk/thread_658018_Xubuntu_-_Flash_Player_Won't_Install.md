---
title: "Xubuntu - Flash Player Won't Install"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by mlhudson on 2008-01-04
Ok, so I did all the standard stuff on a fresh install of xubuntu (7.10) and when I went through the firefox install process for getting flash, it says it installed  -- I could find the package in synaptic, so i think it did -- but all flash required sites still give me the "missing plugin" notice in firefox...

how do I get firefox to use the flash player i installed. 

just for further info, i used acrobat, not gnash (which seemed buggy when I first tried it - - bad job framing videos, etc). 

i'm sure i'm just being dunderheaded, but I don't even know where to start. anyone?

---

### Post by spydon on 2008-01-04
Download the tar.gz from here [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

and then untar it and do ```
sh flashplayer-installer
``` it will ask some questions and the flash player is installed under 1 min.

---

### Post by Crumpets and Jam on 2008-01-04
> **mlhudson said:**
> Ok, so I did all the standard stuff on a fresh install of xubuntu (7.10) and when I went through the firefox install process for getting flash, it says it installed  -- I could find the package in synaptic, so i think it did -- but all flash required sites still give me the "missing plugin" notice in firefox...

how do I get firefox to use the flash player i installed. 

just for further info, i used acrobat, not gnash (which seemed buggy when I first tried it - - bad job framing videos, etc). 

i'm sure i'm just being dunderheaded, but I don't even know where to start. anyone?

Following [these]("http://ubuntuforums.org/showthread.php?p=4012400") steps fixed my problem.

Good luck.

---

### Post by mikewhatever on 2008-01-04
The package for plash player is flashplugin-nonfree. Try the following command and post the output in case something is still wrong. <sudo apt-get install flashplugin-nonfree>

---

### Post by spydon on 2008-01-04
As you can read in Crumpets and Jam's link the flashplugin-nonfree doesn't work as good as the one that you download from the adobe site. I think the one from the adobe site is a newer version too...

---

### Post by lswest on 2008-01-04
yeah, there's a bug with the repo package (md5sum mismatch, probably because the repos arent updated with the new md5sum and checks the new package for the old sum) and hasn't been fixed yet, so get the one off the site and run it like was described above.

---

### Post by mlhudson on 2008-01-04
Will Do! Thanks for ALL the quick answers. I'll post the outcome shortly!
matt

---

### Post by mlhudson on 2008-01-04
AWESOME! Record breaking speed you guys! I put the question in when I went to work. I checked back & fixed the problem on a 30 minute break!

YEAH for Ubuntu!

Thanks guys.

m

---

### Post by owenevl on 2008-01-20
i hope this works for me as well. ive been trying for about 6 hours to get flash on xubuntu =\ it = phail for me lolz ill try this one and pray it works.

---

