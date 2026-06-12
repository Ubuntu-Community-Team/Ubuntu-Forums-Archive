---
title: "When I download something on Ubuntu, should I download the TGZ, RPM, DEB or YUM?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by dninex on 2007-06-29
I keep getting those options, and being a Ubuntu user from only yesterday, I have no clue on how to even install most of the stuff I downloaded. Knowing which one to download may help, so can someone recommend which one I should download for Ubuntu? Thanks in advance.

---

### Post by skyhopper88 on 2007-06-29
You want debs, just like exes for windows. RPMs are similar but they are for other distros that aren't debian based. You can convert rpms into debs with a console program called alien, but only bother with it if there is no deb around. TGZ is like a zip, but it only has the source code and you have to compile it yourself (they're like blueprints to a house)

---

### Post by dninex on 2007-06-29
So if I download an RPM, double clicking will install it? I don't have to bother with terminals, codes or commands at that point?

---

### Post by brownknight on 2007-06-29
choose DEB packages

---

### Post by kakalaky on 2007-06-29
You don't want rpms, you want debs.  Double clicking them will install them, assuming it's dependencies can be met.

---

### Post by dave-5B on 2007-06-29
.deb is the format ubuntu (and any other debian based distro) uses... debian > .deb :) )

in my experience it is almost always better to install things using the repositories (apt-get install foo OR using Synaptic in the System > Administration menu)

also the advantage of a popular distro like ubuntu is that the repositories have every program under the sun

---

### Post by PCFascist on 2007-06-29
> **dninex said:**
> So if I download an RPM, double clicking will install it? I don't have to bother with terminals, codes or commands at that point?

Or @ a terminal type:
```
man alien
```

It will explain how to use alien to covert an rpm to deb then how to install the newly created deb.

---

### Post by dave-5B on 2007-06-29
adding to my last post...
that way you dont have to worry about downloading anything, it does it all for you

btw only the main and restricted repositories are enabled by default most of the good stuff is in teh universe so you have to enable it, easiest way is in synaptic somewhere

---

### Post by bodhi.zazen on 2007-06-29
In general, download from the Ubuntu repositories first.

If it is not in the repositories :

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then update ```
sudo apt-get update
```

If it is not in the repository.

1. Not all .deb will work with Ubuntu, so dl an ubuntu .deb if possible.

2. Not all .tgz are source code. .tgz are archives, like zip files. Some contain binaries. You will need to read the readme.

3. Installing from source requires "build-essential" and possibly additional stuff.

4. Check out checkinstall if building from source : [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

5. Above all else use alien as an absolute LAST resort.

How to install anything : [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by eentonig on 2007-06-29
Before even considering to answer your question. What do you want to do? I suppose you want to install program xyz. 

Dit you use Synaptic to try and install it? If you don't know what Synaptic is, do a search on synaptic or apt-get.

If you did try synaptic and couldn't find the program you want in there, you're best of downloading **.deb** file.

If they fail to offer .deb. you could install alien (via Synaptic) and donwload **.rpm** files

Anything else is going to be too difficult to start with for the moment.

---

