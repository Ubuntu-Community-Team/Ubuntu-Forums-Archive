---
title: "Printer Problems"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-03-15
Hi I'm sorta new to ubuntu so bear with me.  I have an HP PSC 1210 printer/scanner/copier.  I do not have any clue how to set it up or how to get it to work!!! Please help anyone.

---

### Post by Svictor on 2006-03-15
[http://linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1210]("http://linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1210")

The mentioned drivers are availible as packages for ubuntu (install through Synaptic).

---

### Post by Sef on 2006-03-16
Wondering-jew's fix worked for my PSC 1610, so it may work for you:

[http://www.ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1610]("http://www.ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1610")

W_J's post:

> hey I just got my psc 1610 working for both scanning and printing (yay me!)...
first I did

sudo apt-get install hplip gtklp xpp hpijs python-qt3-doc libqt3-mt-mysql hplip-ppds

I don't know if you need all those packages they were all reccomended or suggested and I hate going back and adding things later... then I went to system->administration->printing > printer> add printer and in step 2 I selected psc 1600 from 'HP (HPLIP)' in the manufacturer drop down menu (as opposed to just 'HP' which did make a difference for me ) this got the printing part working.

Then xsane told me it didn't find any scanning devices so I installed a package called libsane-extras from synaptic and tried xsane again and it worked.

---

