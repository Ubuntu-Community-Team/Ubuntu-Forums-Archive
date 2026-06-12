---
title: "i cant install yahoo messenger ?"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by ghostshadow189 on 2006-11-05
hi all,
i want to install yahoo messenger but seem that there no libssl0.9.6 so i cant . s1 help me pls .
thanx

---

### Post by Sef on 2006-11-05
> hi all,
i want to install yahoo messenger but seem that there no libssl0.9.6 so i cant . s1 help me pls .
thanx

Why not use GAIM (Ubuntu) or Kopete (Kubuntu) instead?  Is there a reason you don't want to?

---

### Post by ghostshadow189 on 2006-11-05
because i prefer yahoo messenger :D and want to know how to install it

---

### Post by Sef on 2006-11-05
Have you tried synaptic to download your missing dependency?

system > administrator > synaptic package manager 

and do a search for it.

---

### Post by ghostshadow189 on 2006-11-05
sure , i used it but it just has libssl0.9.7 and libssl0.9.8 . i also saw that libssl0.9.8 is installed by default but it still cant install yahoo messenger .
thanx for ur helps

---

### Post by BWF89 on 2006-11-05
I didn't know Yahoo made their messenger for Linux.

---

### Post by bradleyd on 2006-11-05
xlibs is a dead package, you need to download the dummy package to trick yahoo that it is installed [http://librarian.launchpad.net/4291021/xlibs_dummy.zip](http://librarian.launchpad.net/4291021/xlibs_dummy.zip)
then you will have to find libssl0.9.6(it is outdated) DEbian has it in it's repositories.
or you could just enable universe in your repostory and type apt-get install ymessenger.
hope that helps.---Correction universe also has libssl0.9.6 [http://packages.ubuntu.com/breezy/oldlibs/libssl0.9.6..sorry](http://packages.ubuntu.com/breezy/oldlibs/libssl0.9.6..sorry)

---

