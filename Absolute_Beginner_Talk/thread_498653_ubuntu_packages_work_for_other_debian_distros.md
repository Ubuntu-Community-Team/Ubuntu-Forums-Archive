---
title: "ubuntu packages work for other debian distros?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-07-11
If I wanted to use debian unstable or sidux, would packages made for ubuntu work on them? Or more specifically, would they work well, and there would be no reason to not do so as for minor incompatibilities etc.

Also, although this is the wrong place, do debian packages work on all distros based off it?

It's just that say there is a new unknown bit of software I find and they have a .deb for ubuntu and debian, and a .rpm for fedora etc, they probably won't have one for sidux, which is probably where I am going.

I guess I could compile, but sometimes I really just don't want to...

Sorry for the incoherence of that.

EDIT: Cleared up paragraph.

---

### Post by alanphil on 2007-07-12
I don't think there is an easy "yes/no" answer to your question. It would depend on what Ubuntu packages you are talking about using in Debian. What dependencies do these packages have with the kernel version? Will your Debian install use the same version kernel as your Ubuntu install?

You could try using an Ubuntu package in Debian. I would imagine that the best solution to to compile these packages for Debian -- then you will be positive that they are going to work. You will lose a little time in compiling packages, but you won't be spending so much time experimenting and testing.

---

### Post by bodhi.zazen on 2007-07-12
> **moredhel said:**
> If I wanted to use debian unstable or sidux, would packages made for ubuntu work on them? Or more specifically, would they work well, and there would be no reason to not do so as for minor incompatibilities etc.

Also, although this is the wrong place, do debian packages work on all distros based off it?

It's just that say there is a new unknown bit of software I find and they have a .deb for ubuntu and debian, and a .rpm for fedora etc, they probably won't have one for sidux, which is probably where I am going.

I guess I could compile, but sometimes I really just don't want to...

Sorry for the incoherence of that.

EDIT: Cleared up paragraph.

No, just because it is a .deb does not mean your can install it without problems onto Debian/Ubuntu/Mepis/Linspire/Pioneer etc.

You should build from source :)

If that fails, read this, including the cautions :

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

[http://wiki.serios.net/wiki/Apt-Pinning_on_Ubuntu](http://wiki.serios.net/wiki/Apt-Pinning_on_Ubuntu)

[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

### Post by moredhel on 2007-07-13
ok thanks :)

---

