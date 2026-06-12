---
title: "needs help installing new kernel"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by Blade1357 on 2006-06-27
i have read the tut on how to install the kernel but i am getting an error message when i start the sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev
i get this message W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
need hlp if you can hlp me i adpre. it

---

### Post by professor_chaos on 2006-06-27
My first guess is that you don't have your cd mounted. If you have the right repositories, you should "uncheck" your cd drive repo via synaptic. Or just try inserting and mounting your install cd.

synaptic->settings->repositories

---

