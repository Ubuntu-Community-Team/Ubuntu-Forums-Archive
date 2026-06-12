---
title: "Getting the latest version of OpenOffice"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by BaffledMollusc on 2005-11-09
Hi,

Couldn't decide whether to post this question in the Hoary forums or the Breezy forums, so I decided to put it here, since it's probably a really simple question.

I'm currently using Hoary, with OpenOffice 1.1.3. I'm about to create a presentation that will need good Power Point support, so I'd like to use the latest version of OO that shipped with Breezy.

Is there anyway I can upgrade my OO version without doing a complete dist upgrade (now would be a really, really bad time for the OS to get screwed up, which is why I'd prefer to avoid using dist upgrade).

---

### Post by gord on 2005-11-09
open up synaptic and search for 'openoffice.org2" tag that and click apply. i don't know if thats the version used in breezy (still using hoary too :)) but the diffirences should be neglegable

---

### Post by ssam on 2005-11-09
the openoffice2 from the hoary universe is months older than the one in breezy.

you could probably install just the openoffice pakages from breezy. although i cant promise that this will work.

i think the process would be to add the breezy main repository, update just open office, then disable that repository.

in synaptic go to settings -> repositories. click add

type: binary
uri: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
dist: breezy
section: main

then click ok and ok to get back to the main synaptic window

it should ask you if it can reload the package data, because you added a new repository. if not just click reload.

then update notification applet may tell you that you should download hundreds of updates. ignore it, that would upgrade your system to breezy

then search for openoffice.org2.

right click on openoffice.org2 in the package list and click install

it will then tell you what needs to be done to install openoffice.org2

if you are lucky it should just be installing the openoffice 2 components, this should work and be harmless. if you are unlucky it will want to upgrade huge chunks of your system, if so then this could make lots of stuff stop working and could be messy. if you are not sure let us know.

once you had done that, then remove the breezy repository from settings -> repositories. and everything should carry on as normal.

it may be easier to download the packages from the openoffice website and do an installation independent of the package manager.

---

### Post by BaffledMollusc on 2005-11-09
Thanks Sam.

Unfortunately the package and repository adding in Synaptic isn't as slick in Hoary as Breezy, so I can't follow the instructions you gave to add a repository.

To get around this I added the line
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted
to my etc/apt/sources.list file. 

This seemed to work, and I get the option of installing openoffice.org2. If I tick that, however, it does want to remove and upgrade a large number of packages. Also it wants to remove ubuntu-base and ubuntu-desktop...

Not feeling entirely comfortable with this...

---

### Post by ssam on 2005-11-09
yeah that sounds a bit, much.

i recommend that you go with downloading the binarys from the openoffice site. see this post.

[http://ubuntuforums.org/showthread.php?t=80392](http://ubuntuforums.org/showthread.php?t=80392)

---

### Post by BaffledMollusc on 2005-11-09
Okay, thanks.

---

### Post by BaffledMollusc on 2005-11-09
...And that worked fine. I now have OO 2.0 working happily under Hoary.

Thanks again!

---

