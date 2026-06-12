---
title: "Compile Your Own Kernel - It's Easy!"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by ramjet_1953 on 2007-04-05
Hi, Guys!

I have had an adventure over the past 4 days, learning how to compile my own kernel.

Don't be put off, by thinking it is totally in the realm for geeks.

It's easy and my very first attempt worked, except for me omitting iptabels, which was easily fixed.

The information that unlocked all of this for me is in a free book, which can be downloaded in pdf format and then printed.

The book is: "Linux Kernel In A Nutshell" by O'Reilly and it allowed me to delve into this area that I always thought was a bit on the dark magic side of things, with ease.

Here's the link: [http://www.kroah.com/lkn/](http://www.kroah.com/lkn/)

For instance, you can easily download the latest kernel and to configure it, you just use a graphical configurator which shows the kernel options in a nested tree, like a file manager and you just work your way through and select, or de-select options. The book has a fairly extensive reference guide for each option.

The thing that amazed me is that if you follow the instructions, there is no way that you can damage your existing kernel, or install. It just places another boot option into the GRUB menu, which can easily be edited, or changed back.

I compiled the latest stable kernel for my Edgy install and tailored it specifically for my laptop's Pentium M processor. I also got rid of a lot of stuff that I don't need in my case. The result? A noticably snappier OS!

Give it a go!

Regards,  
Roger :cool:

---

### Post by Spr0k3t on 2007-04-05
Thanks for the encouragement, I may have to try this.

---

### Post by igknighted on 2007-04-05
While I HIGHLY recommend anyone interested in really diving into Linux should try this at some point, please be aware that there are many consequences to running a custom kernel.  For one, many proprietary blobs available in synaptic will cease to work (esp. nvidia/ati/wifi drivers).  Of course these can be installed manually, but you can no longer use the package manager for them.  Also, if you do it wrong your system will not boot.  Don't worry, just pick an older kernel from the grub menu, but be aware this could very easily happen (and usually does the first time or two if you forget to include something important while running xconfig).

In short, its a rewarding process, but do some research first.  Know your hardware REALLY well, because you will have to pick what specific drivers you need included.  Know what drivers will need to be reinstalled (or modules rebuilt).  And know that no matter what, you can always boot into the old kernel, so don't worry too much... the only thing you've got to lose is ~4 hours of time on your computer :)

---

### Post by jvc26 on 2007-04-05
Its good fun, though with the new feisty release I'm not sure whether I need to compile a new kernel yet, as its still loading nice and quickly ;) I might do it at a later date anyway, taking out all the junk I don't use like the bluetooth stuff.
Il

---

