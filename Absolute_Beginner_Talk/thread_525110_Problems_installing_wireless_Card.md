---
title: "Problems installing wireless Card"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by paranoiapenguin on 2007-08-13
Hey guys I know this subject has been brought up time and time again but I can't seem to figue out the directions on some of the posts Im a thick headed n00b who 'll need easy to understand step by step directions if possible.  This is what's wrong.  I have the newest version of Ubuntu feisty fox 7.04, a dell latitude C510/610, and a belkin wieless g notebook card F5D7010 ver 5100 .  I've tried different methods of getting it to work but they don't end up working because I can't get ndiswrapper to work.  Is there anyway someone can help me out either without ndiswrapper o indepth steps using it.  Any help would be much appreciated.

---

### Post by uzerzero on 2007-08-14
Download the driver from Belkin's site here: [http://www.belkin.com/support/article/?lid=en&pid=F5D7010&aid=6003&scid=0&fid=2671&fn=F5D7010_v5.exe]("http://www.belkin.com/support/article/?lid=en&pid=F5D7010&aid=6003&scid=0&fid=2671&fn=F5D7010_v5.exe") Extract it using ```
unzip -a FD57010_v5.exe
```, then locate the .inf file. Under System->Administration->Windows Wireless Drivers, you should be able to get it to load. If not, you may need to install the latest ndiswrapper drivers.

---

### Post by paranoiapenguin on 2007-08-14
Hey,

Thanks uzerzero fo the advice its appreciated, I installed the ndis graphical interface and I went to install the inf file and it didn't do anything.  It was as if it loaded it but after there was nothing in the installed drivers column.  Any advice?

---

### Post by ugm6hr on 2007-08-14
> **paranoiapenguin said:**
> Hey,

Thanks uzerzero fo the advice its appreciated, I installed the ndis graphical interface and I went to install the inf file and it didn't do anything.  It was as if it loaded it but after there was nothing in the installed drivers column.  Any advice?

ndis-gtk doesn't work properly, but it does install the first driver chosen.  You should check if it's installed manually:

```
ndiswrapper -l
```

This also might help (if you haven't seen it already): [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by paranoiapenguin on 2007-08-14
Tada! Im talking to you guys connected to my wireless network.  Sure it was difficult transferring  to ubuntu and picking up the lingo but with your help I was able to set up my internet.  Thanks uzerzero and ugm6hr.  I really appreciate your help

---

