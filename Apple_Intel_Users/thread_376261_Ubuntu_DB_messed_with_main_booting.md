---
title: "Ubuntu DB messed with main booting"
date: 2007-03-04
forum: Apple Intel Users
---

### Post by neutrino15 on 2007-03-04
Hello

Ever since I followed the ubuntu guide to installing Ubuntu on a MacBook, my computer will not boot up unless I hold down the option key at startup and select my internal HD. If I do not hold option, it just freezes at a gray screen (and then after about 5 minutes it goes to OSX). Holding option makes it work fine (so I can choose between OSX and Linux) so this problem is not THAT terrible.. Yet I would like to have OSX be the default OS...

The following BOOT partitions are flagged:

1) A FAT-32 (200mb) i think this is bootcamp...
2) The ext-3 ubuntu partition (8gb)


Both my main OSX partition and the swap partition are not flagged as boot.



Thanks!-
-Neutrino

---

### Post by incubus on 2007-03-04
Have you tried running rEFIt from OS X to fix its installation?

Worst case scenario, you could try the OS X installation disc.  I have very small experience with Macs (this is my first Mac in many many years), but I assume it should have some utility to fix that.

I guess rEFIt should be able to fix it though.

incubus

---

### Post by neutrino15 on 2007-03-04
i installed refit, it did absolutely nothing to help.. Same problem.. and refit does not start... Its not worth it for me to reformat my drive..

---

### Post by Gen2ly on 2007-03-05
You ould try restoring grub.


[Restrore Grub from a LiveCD]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=install+grub+from+live+cd")

If the first tutorial listed doesn't work try the second.

Also try installed rEFIt from the Ubuntu side.

[rEFIt deb]("http://ftp.debian.org/debian/pool/main/r/refit/refit_0.7-3_i386.deb").

---

### Post by neutrino15 on 2007-03-05
Hmm.. I reinstalled rEFIt and made some changes in th config file. It now seems to work fine. Thanks for your help!

---

---

