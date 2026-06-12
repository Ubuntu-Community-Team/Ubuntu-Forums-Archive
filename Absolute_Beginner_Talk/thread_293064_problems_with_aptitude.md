---
title: "problems with aptitude"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-11-04
when trying this:

$sudo aptitude install nvidia-glx-legacy nvidia-kernel-common nvidia-xconfig linux-restricted-modules-`uname -r`

I get this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

What should I do, and what does dpkg --configure -a do?

---

### Post by pay on 2006-11-04
I think that happens when something is installing but you close it before it finishes. It wouldn't hurt to to ```
sudo apt-get install -f
```aswell

---

### Post by CatKiller on 2006-11-04
> **tommy1987 said:**
> What should I do

You should do what it says. Although you'll probably have to run it with **sudo**.

>  and what does dpkg --configure -a do?

**man dpkg**:

>        **dpkg --configure** _package_ ... | **-a** | **--pending**
              Reconfigure an unpacked package.  If **-a** or  **--pending**  is  given
              instead  of  _package_, all unpacked but unconfigured packages are
              configured.


---

