---
title: "How does Ubuntu work with kernels?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Jochus on 2006-08-06
Hi!

I just switched from Gentoo to Kubuntu. I did an upgrade of the system, and GRUB automaticly shows the new kernel. But how can I CORRECTLY remove the old kernel?

---

### Post by steve.horsley on 2006-08-06
Run synaptic, search for linux. Amongst all the kernels you find there, you can remove all but the latest, by right-click and Mark For Removal.

---

### Post by David Corrales on 2006-08-06
Go to Synaptic and search for the old kernel and it's modules, uncheck them and let apt do its magic.

---

### Post by Meck1982 on 2006-08-06
I think just boot into the new one. And than remove the old one with aptitude/apt-get or synatic/apdept manager. It just works like the installation or removal of any other software. Normally the grub entries should be updated automatically.
I have been using kubuntu for a few months only, so I am not 100% sure if this is the best way to do that, but worked perfectly for me.

---

### Post by ajgreeny on 2006-08-06
Always a good idea to keep one known working kernel back from the latest, however, just in case something goes wrong with the new one, then you have a back up kernel to use.  I've never needed to use it but I gather from the forum that some people have.

---

