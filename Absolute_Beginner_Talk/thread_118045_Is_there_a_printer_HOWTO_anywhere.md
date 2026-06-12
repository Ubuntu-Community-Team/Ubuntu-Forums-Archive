---
title: "Is there a printer HOWTO anywhere?"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by lindejos on 2006-01-16
I know that I can probably figure out a HOWTO, I'm just having trouble finding a thread with a howto in it.

I want to connect to a network HP PSC 1610 All-in-one.

---

### Post by halfvolle melk on 2006-01-16
Hi,
Check out this thread:
[http://ubuntuforums.org/showthread.php?t=33576](http://ubuntuforums.org/showthread.php?t=33576)

---

### Post by Sef on 2006-01-16
Wondering_jew's post is great.  Have my PSC 1610 running just fine.

Here is his post:

> hey I just got my psc 1610 working for both scanning and printing (yay me!)...
first I did

**sudo apt-get install hplip gtklp xpp hpijs python-qt3-doc libqt3-mt-mysql hplip-ppds**

I don't know if you need all those packages they were all reccomended or suggested and I hate going back and adding things later... then I went to system-[B]>administration->printing > printer> add printer and in step 2
I selected psc 1600 from 'HP (HPLIP)[/B]' in the manufacturer drop down menu (as opposed to just 'HP' which did make a difference for me ) this got the printing part working.

Then xsane told me it didn't find any scanning devices so I **installed a package called libsane-extras** from synaptic and tried xsane again and it worked.

I didn't have to mess around with the [http://localhost:631](http://localhost:631) or hp-toolbox or any of that (I couldn't when I tried anyways)

---

