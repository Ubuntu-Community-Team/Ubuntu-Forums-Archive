---
title: "problem installing xml parser perl"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by herbert tamayo on 2006-12-04
Hi, I´m trying to install GParted in My breezy (5.10), when I "make it" it says that the "xml parser perl module" is required, so, I downloaded that module but after I did "perl Configure.PL" it says that everything it´s ok, but when I tried "make" it says that expat.h doesn´t exist and after that every line says: XML_Parser didn´t declared....", I just followed the instructions in the readme file but nothing works, what is happenning with that?

-Is there an easier way to install XML Parser?

-why breezy doesn´t come with all those kind of libraries?

-Is there an easier way to install GParted?

---

### Post by Perfect Storm on 2006-12-04
Have you checked synaptic for gparted?

---

### Post by tbroderick on 2006-12-04
gparted is in the repos. Just sudo aptitude install gparted.

---

### Post by herbert tamayo on 2006-12-04
Yes, Ichecked, and the only one that appears is something called "parted" I´m trying to use that tool but it´s console mode, but here is another question: why that applicattion isn´t in the main menu?



> **herbert tamayo said:**
> Hi, I´m trying to install GParted in My breezy (5.10), when I "make it" it says that the "xml parser perl module" is required, so, I downloaded that module but after I did "perl Configure.PL" it says that everything it´s ok, but when I tried "make" it says that expat.h doesn´t exist and after that every line says: XML_Parser didn´t declared....", I just followed the instructions in the readme file but nothing works, what is happenning with that?

-Is there an easier way to install XML Parser?

-why breezy doesn´t come with all those kind of libraries?

-Is there an easier way to install GParted?

---

### Post by tbroderick on 2006-12-04
> **herbert tamayo said:**
> Yes, Ichecked, and the only one that appears is something called "parted" I´m trying to use that tool but it´s console mode, but here is another question: why that applicattion isn´t in the main menu?

Gparted is in the repo. Maybe you should check your /etc/apt/sources.list and make sure all the repo's are enabled. Here is the page at packages.ubuntu.com;

[http://packages.ubuntu.com/breezy/gnome/gparted](http://packages.ubuntu.com/breezy/gnome/gparted)

Parted doesn't show up in your menu cause it's a console program and doesn't have a desktop entry. You could edit the menu and add it if you want to. Just add, 'gnome-terminal -e parted', as the launcher.

---

