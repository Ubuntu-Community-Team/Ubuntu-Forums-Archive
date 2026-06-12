---
title: "I'm such a noob. Possible kernel issues?"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by savemekaizer on 2007-09-29
So, a few days ago I posted a thread about how my internet adapter wasn't working.
That WOULD be resolved and all, but ndiswrapper never installed correctly.
I read the instructions front and back, and I double checked them.

It said I needed to type in a command in the terminal, and look for "include" and a .config file.
It have the include directory, but not a .config file.
I can't use wget to download an updated kernel (2.6), because my internet connection on that computer doesn't work, and when I download a .bz2 file from kernel.org, and try to extract it, it says its not a valid tar file.
Poking around google has told me that i need bzip2, or something along the lines of that.
It comes as a statically linked executable, and when I try to do anything with that, it... doesnt.


Whats going on, and what can I do to fix this mess?

---

### Post by HermanAB on 2007-09-29
Hmm, if you have low level troubles like this, then you should shop around for a different distribution, for example Mandriva, Fedora and Suse.  The reason being that each distro has a different set of installation scripts and a different set of hardware in their labs.  So by trying a different distro you may get lucky and it will all install perfectly on your hardware.

Note that underneath the glitz all distros are the same.  The difference between distros are mostly confined to cosmetics and configuration wizards.

That being said, another option is to spend $10 for a cheap and common ethernet adaptor with either an Intel or a RealTek chip on it.

Eventually, you'll get to know how to fix these issues, but you have to get started somehow, so look for an easier way...

Cheers,

Herman

---

### Post by savemekaizer on 2007-09-29
Aha, so I should start at the basics.
Makes sense; a friend of mine recommended Ubuntu to me because of its user-friendly GUI.
I guess that just because the GUI's friendly, that doesnt mean the rest of the OS is, especially to people who have no clue as to what theyre doing. :P

So I pretty much have to surf around until I find one that doesn't pull that stunt on me upon installation? Great. 
At least I won't be wasting my weekend, as I usually do. :D


I do, however, learn best from doing hands-on things...
whether it be from a rampant failure and learning how to fix said failure, or just someone explaining something to me and me testing it out at home.
I will look around though- Fedora doesn't look half bad.

---

### Post by rickycodie on 2007-09-29
i recommend sabayon it has a lot of drivers loaded natively.

ubuntu is very user-friendly, unfortunately no os (not even windows) works perfectly with every machine.

---

### Post by Gremlinzzz on 2007-09-29
The newest kernel is in gutsy packages its a deb package look under linux-image
[http://packages.ubuntu.com/gutsy/base/](http://packages.ubuntu.com/gutsy/base/)

---

