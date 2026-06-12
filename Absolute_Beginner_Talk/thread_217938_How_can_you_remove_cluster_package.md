---
title: "How can you remove cluster package?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by DThurman on 2006-07-17
Um, yeah... it was installed, sort of.  Installation of clvm actually failed to install.  So trying to uninstall the cluster packages will remove everything BUT clvm....

So, how can I forcably remove clvm?

I tried dpkg -force-all -r clvm and it does not work.

Thanks!

---

### Post by GuitarHero on 2006-07-17
Try uninstalling it with the synaptic package manager.

---

### Post by DThurman on 2006-07-17
I tried that.  Same error.

That is why I resorted to using debian's package commands to try to force the removal of this package.

---

### Post by DThurman on 2006-07-17
Ok.... I solved the problem.

The /var/lib/dpkg/info/{pre,post}rm scripts are messed up.  I simply edit these two files and removed the if blocks and then ran dpkg --purge clvm and was able to remove this package.

Also, I had to run:

find / -name \*clvm\* -exec rm -f {} \; -print

to get rid of the extraneous left over files...

What a chore.

Someone needs to look into this and fix it.

---

