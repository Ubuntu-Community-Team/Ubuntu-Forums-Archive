---
title: "Bootsplash on PPC"
date: 2005-05-01
forum: Apple PPC Users
---

### Post by Ptero-4 on 2005-05-01
Hi. I wanted to know. Does the Hoary PPC kernel support bootsplash? If it does, what I need to install to make it work? If it doesn't what I need to do to make it support bootsplash (or how to do to compile a fully working kernel, I have never compiled a full kernel and the closest thing to that is the mol-kmods)?

Thanks.

---

### Post by Len on 2005-05-05
Get the 'linux source' from Synaptic. It will be placed in /usr/src. Untar the archive and make a softlink named linux in the /usr/src dir: ln -s /usr/src/linux-2.7-10(...)/ /usr/src/linux .
Cd to the linux source directory and go read some documentation. You can find enough on Google as well. If you think you can do the job, just type "make menuconfig" to configure your kernel build. You can compile the little penguin boot splash in it.

[http://www.linuxplanet.com/linuxplanet/tutorials/202/1/](http://www.linuxplanet.com/linuxplanet/tutorials/202/1/)
[http://www.freeos.com/articles/2589/](http://www.freeos.com/articles/2589/)
[http://www.google.nl/search?hl=nl&q=compile+linux+kernel&btnG=Google+zoeken&meta=](http://www.google.nl/search?hl=nl&q=compile+linux+kernel&btnG=Google+zoeken&meta=)

Happy reading ;-). It isn't hard, but to be safe you'd better create a new Yaboot boot menu (or save the old kernel in BootX) to be sure you can revert if your kernel doesn't work properly. The man pages of Yaboot are very straigtforward.

There is an issue with a missed dependency with the pmac ATA drivers. If you get a build error you have to check the generic ATA support or so, Google is again your friend here. If you wonder about drivers you need for your mac feel free to ask. My powermac G4 for example used the "sungem" driver for the ethernet NIC. Took me some time to find out... lsmod and other utilities should help you avoid such a mistake.

Good luck!

---

