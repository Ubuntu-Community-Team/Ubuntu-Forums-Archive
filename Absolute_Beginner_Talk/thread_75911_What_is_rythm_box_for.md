---
title: "What is rythm box for?"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-10-14
It doesnt seem to want to play anything, mp3, wma, ogg, rm etc etc etc
Also im sure when i first installed ubuntu there was a lot more in the Synaptic (including an mp3 player?)
Now it seems the list has shrunk dramatically

---

### Post by clparker on 2005-10-14
For Various Legal Reasons, you have to install the codecs separatly. It's pretty easy, first you have to basically enable the universe repository.  and install gstreamer-plugins.

check out ubuntuguide.org that place rules

stick with us kiddo, we're goin' places. Linux isn't allways point and click easy, but it blows microsoft away in terms of security, stability, and well everything else.

---

### Post by dgrafix on 2005-10-14
What does this mean:
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

These are the sources i have in my wotsit file:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

---

### Post by Jussi Kukkonen on 2005-10-14
[QUOTE=dgrafix]What does this mean:
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

These are the sources i have in my wotsit file:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/[/QUOTE]
dgrafix, You'll need to add the universe-repository. You'll find instructions at ubuntuguide (although they might still refer to hoary repositories, fix that if you use breezy).

---

