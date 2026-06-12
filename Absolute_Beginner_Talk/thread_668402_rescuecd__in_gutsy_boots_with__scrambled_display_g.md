---
title: "rescuecd  in gutsy boots with  scrambled display green vertical strips"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by LarryJ2 on 2008-01-15
My systemrescuecd-x86-0.4.2  bootable iso CD that  I downloaded and burned always booted in the graphical mode  with a scrambled display.  After considerable gnashing of teeth and pulling of hair,  here's what fixed it for me.

At the **boot:** prompt  enter the following after the prompt so it looks like this

>  rescuecd doxdetect forcevesa

Then later when you get the **root@rescuecd /root %** prompt enter

> startx

which launches the graphical user interface containing gparted.

The attached camera shot shows the scrambled  hosed up monitor screen before I applied the fix at the boot: prompt.

FYI   partimage is a text based program so you enter "partimage"  before you  enter "startx".   Startx launches into a graphical mode where one of the icons on the right side starts the  graphical  partition manager gparted.

I never experienced this problem before until I replaced my giant CRT with a SamSung SyncMaster 216BW  so I suspect the SyncMaster doesn't know how to sync afterall.  I hereby demote them to SyncMaster novice.

"rescuecd" is available here:  [http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)

---

