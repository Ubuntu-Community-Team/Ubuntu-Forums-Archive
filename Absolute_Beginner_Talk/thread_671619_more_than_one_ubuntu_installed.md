---
title: "more than one ubuntu installed?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by muuwt1 on 2008-01-18
i have a duel boot with windows xp and ubuntu but at the boot screen it says

Ubuntu, kernel 2.61.17-12-generic
Ubuntu, kernel 2.61.17-12-generic (recovery mode)
Ubuntu, kernel 2.61.17-10-generic
Ubuntu, kernel 2.61.17-10-generic (recovery mode)
Ubuntu memtest86+
Windows XP PRO

should there just be one set of ubuntu and its recovery mode? i use the -12 one. i was also thinking about installing 7.10 and was wondering how this will effect it.

-muuwt

---

### Post by ThrobbingBrain66 on 2008-01-18
There are just two kernels installed.  The old version can be removed with synaptic.

---

### Post by dwblas on 2008-01-18
Your original install of Ubuntu installed the 2.6.17-10 kernel.  One of the updates installed a new kernel, which is the 2.6.17-12 kernel, so both are now installed.  If for some reason the newer kernel doesn't work, you can boot into the older kernel.  I generally start deleting kernels after 2 or 3 are installed.  They are linux-image in Synaptic.  

If you install another Ubuntu on another partition/drive, it will show up on the boot menu as well.  Your existing Ubuntu install will show up as, "kernel 2.6.17-12-generic (on dev/hda2)" or where ever it is.  That is, you will now have a triple boot.

---

### Post by muuwt1 on 2008-01-18
when i install 7.1 can i overwrite my old version of do i have delete my old one and install on a clean drive?

---

### Post by dwblas on 2008-01-20
Part of the install is to format the drive you will be installing to.  This will erase/re-format the drive.  If you don't have a separate partition for /home then you should back up the directory to keep any settings that you have.

---

