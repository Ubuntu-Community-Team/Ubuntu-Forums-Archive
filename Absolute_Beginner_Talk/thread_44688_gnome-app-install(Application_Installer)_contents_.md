---
title: "gnome-app-install(Application Installer) contents not loading"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by koyi on 2005-06-27
Hi, I have this strange problem with the Application Installer(Applications -> System Tools -> Add/Remove Programs). It only shows me the busy mouse cursor without loading the contents(the list of applications). Well, it does bring me to Synaptic when I click on the "Advanced" button.

What is wrong?
Is there something I can do to fix this?
By the way I think it worked before but I dunno exactly when it stopped working.

Thanks.

---

### Post by koyi on 2005-06-27
I found the answer myself  \\:D/ 
It seems to be a dependency bug.
(ref.: [https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871))

So the only way is to wait for the upgrade for gnome-app-install, I guess.

Thanks.

---

### Post by bier444 on 2005-06-30
hy

>It seems to be a dependency bug.

this bug is caused by smeg, that is not very nice. ther is a problem with python-xdg, ...

>(ref.: [https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871))

>So the only way is to wait for the upgrade for gnome-app-install, I guess.

or you have another look at the above link.
i've uploaded a patched version of gnome-app-install-20050404v2, which works well.
the new version is gnome-app-install-20050404v3.
please use the updated version from 06-30-2005.
the install script is ALPHA, but maybe works well. no warranty!

bier444

---

### Post by bier444 on 2005-07-10
hy

i worked on the install-script, the first version did not work correctly. sorry for that. this is the new version (beta state). it should do now the correct install thing.

bier444

---

