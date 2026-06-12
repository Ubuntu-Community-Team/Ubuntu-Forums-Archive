---
title: "Installing programs"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by ffluff on 2007-12-25
Today I'm gonna try yet again to install my very first program.

I have yet to find a program that I'm interested in installing that's been denied from me. 
I have chosen: SMPlayer

Add/remove says I'm not touching that one maybe Synaptic Package Manager will. So I go there mark for installation and get:

Could not mark all packages for install or upgrade.

smplayer:
 Depends: kdelibs4c2a (>=4:3.5.7-1) but it is not installable
 Depends: libqt3-mt (>=3:3.3.8really3.3.7) but it is not installable
 Depends: mplayer

What I make of this message: Here is the list of additional files you'll need but they can't be installed either. I get that for every program I've ever wanted to install. What am I doing wrong?

---

### Post by Spike-X on 2007-12-25
Do you have all your repositories enabled?

In Synaptic, go to Settings > Repositories, and check everything.

---

### Post by RomeReactor on 2007-12-25
Hi. You don't mention which version of Ubuntu you have; if it's an older version, that would probably explain why you can't install the packages. I gather you're running Edgy or a previous version (the version of kdelibs4c2a in Feisty is 4:3.5.6, and libqt3-mt for Feisty is the right one, but for Edgy is 3:3.3.6). It looks like you added a repository not intended for your version of Ubuntu; you can find versions of smplayer for Dapper, Edgy and Feisty [here]("http://wesley.debianbox.be/packages/").

---

### Post by Sordelka on 2007-12-25
First:

Enable all repositories in Synaptic Manager - settings - repositories. In third party software, check everything.

Afterwards try installing again.

---

### Post by ffluff on 2007-12-25
> First:

Enable all repositories in Synaptic Manager - settings - repositories. In third party software, check everything.

Afterwards try installing again.

Ah! Success!

---

### Post by rvm4000 on 2007-12-25
> **ffluff said:**
> smplayer:
 Depends: kdelibs4c2a (>=4:3.5.7-1) but it is not installable
 Depends: libqt3-mt (>=3:3.3.8really3.3.7) but it is not installable
 Depends: mplayer


That version of smplayer must be very old. The new ones don't depend on kdelibs or libqt3 (it depends only on libqt4).

I suggest you to install the latest version available: [smplayer_0.5.62+SVN-r524_i386.deb](http://downloads.sourceforge.net/smplayer/smplayer_0.5.62%2BSVN-r524_i386.deb)

---

