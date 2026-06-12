---
title: "Problem using restricted drivers manager"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Spartan22x on 2007-12-23
I just installed Ubuntu Gusty on an older laptop with a broadcom 43xx wireless card. I'm trying to use the restricted drivers manager to install the restricted drivers for it, but it's not working. While the driver shows up, when I check the box to enable it and confirm, a dialogue box pops up and tells me that "The software source for the package bcm43xx-fwcutter is not enabled", and the only option it gives me is to close the box. What can I do to enable wireless on this computer?

---

### Post by Rocket2DMn on 2007-12-23
go to System->Administration->Synaptic Package Manager then go to Settings->Repositories and make sure the boxes are checked for Universe, Multiverse, and Restricted.  These will enable the repositories so you can download the drivers you need (you probably just need Restricted, but the others are good to have, too).

---

### Post by Spartan22x on 2007-12-23
Thanks, that worked perfectly :)

---

