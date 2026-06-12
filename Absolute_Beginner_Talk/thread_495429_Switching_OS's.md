---
title: "Switching OS's?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Bofur on 2007-07-08
Hi, this may sound like a newbie question but I was wondering if I installed regular ubuntu, could I download some update to switch it to Kubuntu, or do I have to download a whole other OS just to get it. Thanks

---

### Post by cwood06 on 2007-07-08
you can install KDE though the command line,

```
sudo apt-get install kde
```

---

### Post by Bofur on 2007-07-08
And this will switch Ubuntu to Kubuntu?

---

### Post by jrusso2 on 2007-07-08
> **Bofur said:**
> And this will switch Ubuntu to Kubuntu?

It will allow you to use the KDE desktop with Ubuntu which in my opinion is better then Kubuntu.  Ubuntu is better developed and has a better mix of applications.  But i prefer KDE so instead of using Kubuntu I use Ubuntu and add the Kubuntu desktop.

This didn't work so well with feisty though which is one of the reasons I stay with edgy.

---

### Post by pardesi on 2007-07-08
use
```
sudo aptitude install kde-core
```
 instead it takes less time space and  is almost the same and easily removable

---

### Post by AnRa on 2007-07-08
If you want Kubuntu use:
```
sudo apt-get install kubuntu-desktop
```

---

### Post by BL00dFox on 2007-07-08
> **AnRa said:**
> If you want Kubuntu use:
```
sudo apt-get install kubuntu-desktop
```

IMO, Its better to use Ubuntu and install KDE. Ubuntu just feels a lot more pleasurable to use in some way...

---

### Post by Sef on 2007-07-08
Read [Install KDE]("http://www.psychocats.net/ubuntu/kde") by Psychocat.

---

### Post by AnRa on 2007-07-08
> **BL00dFox said:**
> IMO, Its better to use Ubuntu and install KDE. Ubuntu just feels a lot more pleasurable to use in some way...I agree with you, but if he wants Kubuntu then there it is! ;)

---

### Post by Wim Sturkenboom on 2007-07-08
Just out of curiosity:

what's the difference between the three suggested methods above?

---

### Post by AnRa on 2007-07-08
> **Wim Sturkenboom said:**
> Just out of curiosity:

what's the difference between the three suggested methods above?Each method installs a different set of packages.

---

### Post by AlexenderReez on 2007-07-08
> **AnRa said:**
> Each method installs a different set of packages.

my opinion is to use --->

sudo aptitude install kubuntu-desktop

instead of

sudo apt-get install kubuntu-desktop

i don't think it will install difference package as kubuntu-desktop had been set it dependencies...
if you install

 > sudo aptitude install kubuntu-desktop

to remove kubuntu

just 

> sudo aptitude remove kubuntu-desktop

but

by install
using

> sudo apt-get install kubuntu-desktop

remove

> sudo apt-get remove kubuntu-desktop

**only remove meta package ..not all package that you have install for kubuntu-desktop**

---

### Post by Wim Sturkenboom on 2007-07-08
> **AnRa said:**
> Each method installs a different set of packages.I do understand that, but as a simple user, I don't know what I will need. Even using synaptic does not (always) give the answer. From the description for kubuntu-desktop
> 
Kubuntu desktop system
This package depends on all of the packages in the Kubuntu desktop system

It is safe to remove this package if some of the desktop system packages are
not desired.

Will desktop include the koffice or not? Will kde-core give me the look and feel or will only kde give that?

Please note, I'm not interested at all in installing KDE, but I'm just curious and it might help topic starter to take a decision.

---

### Post by AnRa on 2007-07-08
> **reez0105 said:**
> my opinion is to use --->

sudo aptitude install kubuntu-desktop

instead of

sudo apt-get install kubuntu-desktop

i don't think it will install difference package as kubuntu-desktop had been set it dependencies...
if you install

 
to remove kubuntu

just 


but

by install
using



remove



**only remove meta package ..not all package that you have install for kubuntu-desktop**Try this:
```
sudo apt-get autoremove kubuntu-desktop
```
 ;)

Also, apt-get will install less packages by default as it does not install the recommended ones.

---

