---
title: "Module.symvers problem (installing patch)"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by macogw on 2006-07-20
I'm trying to install a driver for my ethernet card.  I'm using the readme, everything was going fine, and then it couldn't compile the external module that was being created.  Reading the install.log file, the problem is that I'm missing the Module.symvers file in the /usr/src/linux folder that is apparently necessary to create an external module.  There is a patch for the kernel here: [http://lwn.net/Articles/81399/](http://lwn.net/Articles/81399/).  That makes perfect sense to me.  I just need to know how do I apply that patch now?  Is it a simple matter of copying and pasting that text into the kernel source, or is it more involved?

 well there's another one [here](http://lwn.net/Articles/79984/) too and I'm not sure which I should be using

---

