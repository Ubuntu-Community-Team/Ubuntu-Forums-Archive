---
title: "philips wireless adaptr snu 6600"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by komikimben on 2008-03-14
hi everyone.
l need your help. l can not use wirellss connection while l am using ubuntu.. because there is no driver for ubuntu. l try to use ndiswarapper  but &#305;t needs internet. there is no way to use internet when  ubuntu run like cable.
please help me...

---

### Post by MadMedis on 2008-03-14
Do you already have ndiswrapper installed?  If not, the ndiswrapper project provides a fantastic set of instructions here:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

I've had good luck with the binary package from the ubuntu repositories, and if you use it, you can skip down to the "compile and install" section of the instructions.  Whether you decide to install the binary or from source, either can be transferred to your ubuntu computer with a USB flash drive, and as long as you have the windows driver for your wireless adapter (see the instructions for details on how to get them), you should have all you need to get the adapter installed.

If you have already installed ndiswrapper, it's a good idea to go through the instructions and make sure you did it right.  If you still have problems after that please post details on what the problem.

---

