---
title: "Grrrr, mounting"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by linuxbun on 2006-12-04
Is there a way I can mount without being root?

I'm trying to mount a network folder, if I mount it manually it appears as a white icon which I can't open, if I put it in fstab, it says that only root can open it ](*,)

---

### Post by bernied on 2006-12-04
Try adding the user or users option to the fstab entry. If you can't work it out, post the fstab entry here.

From man mount:
> .
.
**nouser**
    Forbid an ordinary (i.e., non-root) user to mount the file system. This is the default.
.
.
.
**user**
    Allow an ordinary user to mount the file system. The name of the mounting user is written to mtab so that he can unmount the file system again. This option implies the options noexec, nosuid, and nodev (unless overridden by subsequent options, as in the option line user,exec,dev,suid). 
**users**
    Allow every user to mount and unmount the file system. This option implies the options noexec, nosuid, and nodev (unless overridden by subsequent options, as in the option line users,exec,dev,suid).
.
.

---

