---
title: "its all gone wrong"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by bluemarble on 2006-09-07
I am recent to linux and drapper and have had trouble getting DVDs to play. so I started playing around with things and it all went wrong. I cannot do anything in SPM or terminal without getting this messgae;

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

how do i fix it manually?

---

### Post by monktbd on 2006-09-07
try to do what it says:

open a terminal and type/copy-paste

> sudo dpkg --configure -a

hth

---

### Post by bluemarble on 2006-09-07
Arrr, forgot to mention in the original post that when I try 

'sudo dpkg --configure -a'

I get

Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...

and nothing else happens...

---

### Post by monktbd on 2006-09-07
hmmm try to uninstall/reinstall the flashplugin

> sudo dpkg -r flashplugin-nonfree

not sure if this will help.

---

