---
title: "HP PhotoSmart 1100"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by Ronnie on 2006-03-18
Hello, hope y'all are having a wonderful day.
Has anyone had any trouble connecting a printer to Ubuntu 5.10?
I have a HP PhotoSmart 1100 and want to install it and share it on my Windows network so we don't have to print to my new photo printer all the time. I am wondering if Ubuntu has drivers and if it don't where can I get them?
Thanks for any help.

Ronnie

---

### Post by Sef on 2006-03-18
Wondering_Jew had a solution for his PSC 1600.  Your photosmart uses the HPLIP driver, so should work for you.

> ey I just got my psc 1610 working for both scanning and printing (yay me!)...
first I did

sudo apt-get install hplip gtklp xpp hpijs python-qt3-doc libqt3-mt-mysql hplip-ppds

I don't know if you need all those packages they were all reccomended or suggested and I hate going back and adding things later... then I went to system->administration->printing > printer> add printer and in step 2 I selected psc 1600 from 'HP (HPLIP)' in the manufacturer drop down menu (as opposed to just 'HP' which did make a difference for me ) this got the printing part working.

Then xsane told me it didn't find any scanning devices so I installed a package called libsane-extras from synaptic and tried xsane again and it worked.

[http://www.ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1610]("http://www.ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1610")

---

