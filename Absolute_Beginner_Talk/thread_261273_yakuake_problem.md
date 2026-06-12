---
title: "yakuake problem"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-09-20
I just installed yakuake and it is giving me problems, mainly when I pull a menu down it leaves the trails on the screen how could I fix that and if i cant how do I get rid of the program using apt-get (also including the kdelibs that I had to install with it???)

---

### Post by Rashid584 on 2006-10-28
do sudo apt-get remove yakuake

I wouldnt be fussed about the kde libs, they're probably negligible in terms of memoery or whatever, but if you really are bothered, next time I recommend using aptitude instead of apt-get. It remembers what was installed and removes it with the package too

e.g. sudo aptitude install yakuake, sudo aptitude remove yakuake

-Rashid

---

