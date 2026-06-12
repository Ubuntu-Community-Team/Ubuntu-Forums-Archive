---
title: "Feisty - How to hide update in update manager"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Gus_T_Reer on 2007-06-01
Hi,

I installed beryl/emerald from download.tuxfamily.org and everything is working fine.

The repositories are in sources.list and I received updates via update manager. I installed the updates except the compiz files and those files now show under Others in update manager and update manager doesn't nag me about them which is fine.

However I received another update notification the other day from the same repository (for libdecoration0) which I don't want. I've tried deselecting it (as I did with the compiz files) but it keeps showing up as an outstanding update in update manager.

I don't want to deselect the repositories so how do I tell update manager to ignore that package (or any package I don't want updating) without being nagged when the system restarts.

TIA

---

### Post by F-3582 on 2007-06-01
Run Synaptic and select libdecoration0 (or any other package you don't want to be updated). Then select "Package" -> "Lock Version" and the Update Manager should stop nagging you.

BTW: Why do you want to keep that old version?

---

### Post by Gus_T_Reer on 2007-06-01
Thanks for the prompt reply.

Yup, lock version will do that but the compiz files that don't nag are not locked so I can't work out why thery're not nagging and this one file is.

As to why I don't want to update, the version of libdecoration0 that I have came when I installed Feisty and is used by the compiz which came with Feisty. I haven't updated compiz as I don't use it so see no need to update dependent libararies. Just my little foible.

---

### Post by steeleyuk on 2007-06-01
> I haven't updated compiz as I don't use it

Would it not be better to uninstall Compiz then via synaptic?

---

### Post by Gus_T_Reer on 2007-06-01
Probably, but to be honest that's getting away from the point.

What if I wanted to update a file from the standard Ubuntu repository (say for security updates) but not from a third party repository (which also supplies the file, that I don't want, and also other files that I do want). Locking the file would prevent update notifications from both repositories which is not what is wanted.

I can see that I've explained it as clear as mud. :)

---

### Post by zvacet on 2007-06-01
> Probably, but to be honest that's getting away from the point.

No,that´s the point.If you don´t use some programs why don´t you uninstall it?No harm will be done to you.

---

### Post by Gus_T_Reer on 2007-06-01
Ok, let's forget the reason. I agree with the points being made that it would be easier, and probably more efficient to delete the packages I'm not using.

But, what I'm trying to find out is how update manager has "somehow" put a number of packages on the backburner, they are not locked and it doesn't nag me about them but it does show them and will still allow me to install them by doing a partial upgrade. I have another package from the same repository as those other packages that I can't get on that backburner, I still get nagged and I would like to know how to reproduce the situation with this additional file.

In essence I am trying to understand some functionality within the update manager, not trying to resolve any one particular problem.

---

