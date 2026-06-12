---
title: "slow performance after adding repositories"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by justinesalo on 2006-04-05
hi there,

i like ubuntu a lot and have had a lot of fun working with it, but i've done something stupid that i can't figure out how to fix:

i added debian unstable repositories and upgraded things.  since then, my computer (particularly firefox) is going painfully slow.  i know libfame-0.9 keeps breaking, but i doubt that's the cause of all of it.  is there anyway to revert back to the breezy stuff without completely reinstalling ubuntu?  could i just uninstall and force the version in the reinstall in synaptic? it seems like that would make my computer inoperable before i got the chance to reinstall, no?

sorry for being such a noob, and thanks in advance for any help.

---

### Post by dcstar on 2006-04-05
[QUOTE=justinesalo]hi there,

i like ubuntu a lot and have had a lot of fun working with it, but i've done something stupid that i can't figure out how to fix:

i added debian unstable repositories and upgraded things.  since then, my computer (particularly firefox) is going painfully slow.  i know libfame-0.9 keeps breaking, but i doubt that's the cause of all of it.  is there anyway to revert back to the breezy stuff without completely reinstalling ubuntu?  could i just uninstall and force the version in the reinstall in synaptic? it seems like that would make my computer inoperable before i got the chance to reinstall, no?

sorry for being such a noob, and thanks in advance for any help.[/QUOTE]
Try removing that repository in Synaptic, then do the update and see what "local" package versions you then have installed.

You should be able to select each incorrect package and specify what version you want to install - of course you should select whatever Breezy version you are offered.

---

### Post by justinesalo on 2006-04-05
thanks for answering.  the thing is, i installed/upgraded a lot of packages and am not sure what they all were.  is there any way to find out the difference between the packages that are installed and those that are provided by the (now only breezy) repositories?

---

