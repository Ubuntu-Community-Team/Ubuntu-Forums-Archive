---
title: "XFCE Fails to install"
date: 2009-02-04
forum: Arch and derivatives
---

### Post by &#32 Greg on 2009-02-04
On the use of pacman -S xfce4, (with everything), I get the following:

resolving dependencies...
warning: provider package was selected (freeglut provides glut)
looking for inter-conflicts...
error: unresolvable package conflicts detected
error: failed to prepare transaction (conflicting dependencies)
:: xfce4-settings: conflicts with xfce-mcs-manager

Not sure what to do about this... obviously running TWM is no-one's choice for a WM, and XFCE is my preferred.

---

### Post by smartboyathome on 2009-02-04
Remove xfce-mcs-manager?

---

### Post by &#32 Greg on 2009-02-04
Then it picks a different dependency to fail on, saying it conflicts, and when I tried removing that in addition it still said the same conflict, despite the fact that it wasn't even there.

---

### Post by Grant A. on 2009-02-04
Did you bork something during the Arch Linux install? I have had pacman screw up in the past due to the rc.conf and hosts file not having the same hostname.

---

### Post by &#32 Greg on 2009-02-04
> **Grant A. said:**
> Did you bork something during the Arch Linux install? I have had pacman screw up in the past due to the rc.conf and hosts file not having the same hostname.

Well, I'd say that it's definitely possible (first time Arch, or any real Linux install) but after correcting that, the problem is still continuing.

---

### Post by mips on 2009-02-05
Greg,

Do you have the testing repository enabled? If 'yes' then disable it to install xfce 4.4

You actually have an option here, you can either install v4.4 or v4.6. v4.6 resides in testing and I suspect that is where the conflict originates from as some of the files have changed name since 4.4

Alternatively just install 4.6 if you are ok with that, you will probably have to disable the normal 4.4 repo but I'm not sure.

[http://bbs.archlinux.org/viewtopic.php?id=64506](http://bbs.archlinux.org/viewtopic.php?id=64506)

---

### Post by &#32 Greg on 2009-02-05
> **mips said:**
> Greg,

Do you have the testing repository enabled? If 'yes' then disable it to install xfce 4.4

You actually have an option here, you can either install v4.4 or v4.6. v4.6 resides in testing and I suspect that is where the conflict originates from as some of the files have changed name since 4.4

Alternatively just install 4.6 if you are ok with that, you will probably have to disable the normal 4.4 repo but I'm not sure.

[http://bbs.archlinux.org/viewtopic.php?id=64506](http://bbs.archlinux.org/viewtopic.php?id=64506)

Thanks mips, that did it :)

Now to figure out the ins and outs of this thing.

---

