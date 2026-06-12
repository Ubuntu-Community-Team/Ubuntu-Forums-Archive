---
title: "How to configure printer?"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by Joy on 2006-03-17
Hi,
Please help me to configure and setup hp Deskjet-1120C printer. I have installed Ubuntu 5.10.
Thanks.

---

### Post by Sef on 2006-03-17
Wondering_Jew had a fix for his PSC 1610, it should work for you since they both use the HPLIP driver.  

> hey I just got my psc 1610 working for both scanning and printing (yay me!)...
first I did

sudo apt-get install hplip gtklp xpp hpijs python-qt3-doc libqt3-mt-mysql hplip-ppds

I don't know if you need all those packages they were all reccomended or suggested and I hate going back and adding things later... then I went to system->administration->printing > printer> add printer and in step 2 I selected psc 1600 from 'HP (HPLIP)' in the manufacturer drop down menu (as opposed to just 'HP' which did make a difference for me ) this got the printing part working.

Then xsane told me it didn't find any scanning devices so I installed a package called libsane-extras from synaptic and tried xsane again and it worked.

---

### Post by rjwood on 2006-03-17
go to >system>administration>printing..rt click on 'new printer" then "add printer" then you can see if it detected your printer.(it should have if you had it pluged in and turned on when you restarted last time)...

---

### Post by Joy on 2006-03-25
sorry for delay I was out of station. Now my printer is working. Thanks.
Joy.

---

