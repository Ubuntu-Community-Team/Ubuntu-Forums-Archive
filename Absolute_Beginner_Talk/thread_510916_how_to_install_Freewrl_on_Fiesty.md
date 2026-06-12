---
title: "how to install Freewrl on Fiesty?"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by _stanz_ on 2007-07-27
Hi i need some help. I need to install Freewrl but found no clear documentation on installing it.

The best i can find is : [http://freewrl.sourceforge.net/ubuntu606.html](http://freewrl.sourceforge.net/ubuntu606.html)
But it maybe outdated. Is there a more definite method?

Synaptic doesnt work thou..

---

### Post by noof on 2007-07-27
Hmm, seems like it was removed after breezy. Try and download if from here:
[http://packages.ubuntu.com/breezy/graphics/freewrl](http://packages.ubuntu.com/breezy/graphics/freewrl)

That is, 32-bit:
[http://fr.archive.ubuntu.com/ubuntu/pool/universe/f/freewrl/freewrl_1.07-1_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/universe/f/freewrl/freewrl_1.07-1_i386.deb)
64-bit:
[http://fr.archive.ubuntu.com/ubuntu/pool/universe/f/freewrl/freewrl_1.07-1_amd64.deb](http://fr.archive.ubuntu.com/ubuntu/pool/universe/f/freewrl/freewrl_1.07-1_amd64.deb)

Don't know if you can double-click it in nautilus, if you can't you have to fire up a terminal and write:
sudo dpkg -i /home/stanz/freewrl_1.07-1_i386.deb

Or wherever you've placed the deb. Dunno if it'll work though :)

---

### Post by elektronaut on 2007-07-28
Those packages are all also on the project page: [http://freewrl.sourceforge.net/download.html](http://freewrl.sourceforge.net/download.html)

---

