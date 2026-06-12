---
title: "reinstalling dpkg"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-10-22
I've got problems it seems with dpkg as anyone would know from my report of synaptic update problem.

sudo dpkg --configure -a
dpkg: error processing lame (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 lame


Seems that dpkg is somehow involved and got stuck with 'lame' 
Can someone say how to reinstall as is being recommended?

Many thx in advance.

Macdui! You know this one?!

--
sophtpaw

---

### Post by aysiu on 2005-10-22
It sounds as if it's asking you to reinstall *lame*, not *dpkg*. If that's the case, I'd ```
sudo apt-get install lame
```

---

### Post by sophtpaw on 2005-10-22
[QUOTE=aysiu]It sounds as if it's asking you to reinstall *lame*, not *dpkg*. If that's the case, I'd ```
sudo apt-get install lame
```[/QUOTE]

Thx Aysiu,

Long time! I think it's sorted now:???: 

so long,

--
sophtpaw

---

