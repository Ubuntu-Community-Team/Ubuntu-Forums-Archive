---
title: "Amarok won't play audio cd in Edgy"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by l0k1_ on 2007-02-07
I installed the latest Amarok just fine last night only to discover it won't play any audio cd's while Rythmbox will. I looked around and found this solution - will this work? I don't want to install KDE in place of Gnome just to use Amarok: 

If you don't have KDE installed, you probably have to install kdemultimedia-kio-plugins and it will work ---> apt-get install kdemultimedia-kio-plugins:


... and just wondering would NOT doing the following probably cause Amarok not be able to play cds in ubuntu? i might have forgotten to do these although the package installed just fine without them:

deb [http://kubuntu.org/packages/amarok-144](http://kubuntu.org/packages/amarok-144) edgy main

wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg) | sudo apt-key add kubuntu-packages-jriddell-key.gpg

---

### Post by etank on 2007-02-07
Take a look at this link [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats).

---

