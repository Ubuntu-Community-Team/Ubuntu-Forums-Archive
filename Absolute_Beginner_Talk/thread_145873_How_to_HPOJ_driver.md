---
title: "How to HPOJ driver"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by catlett on 2006-03-17
On install, setup recommended I should install the HPOJ driver. My printer(HP PSC 1510 all-in-one) does not work with the driver that the Ububtu installation used as default. My problem comes when I went to opensource to get the driver. The driver comes in many ways. Compiled, precompiled etc. I am totally ignorant of these things. I am a slave to Redmond. If I can't double-click to activate the windows installer I can't do much. My main question is...The HPOJ page mention "your distribution may have a precompiled HPOJ driver package". Does Ubuntu have the HPOJ driver somewhere on it's support page? I couldn't find it.Thank you.

---

### Post by Sef on 2006-03-17
This should help you, it's from wondering_jew:

> hey I just got my psc 1610 working for both scanning and printing (yay me!)...
first I did

sudo apt-get install hplip gtklp xpp hpijs python-qt3-doc libqt3-mt-mysql hplip-ppds

I don't know if you need all those packages they were all reccomended or suggested and I hate going back and adding things later... then I went to system->administration->printing > printer> add printer and in step 2 I selected psc 1600 from 'HP (HPLIP)' in the manufacturer drop down menu (as opposed to just 'HP' which did make a difference for me ) this got the printing part working.

Then xsane told me it didn't find any scanning devices so I installed a package called libsane-extras from synaptic and tried xsane again and it worked.

[http://www.ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1610]("http://www.ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1610")

---

### Post by catlett on 2006-03-17
Thank you for taking the time to help.     Regards, Catlett

---

### Post by DougTheTyro on 2006-03-26
Worked for me too!!

---

