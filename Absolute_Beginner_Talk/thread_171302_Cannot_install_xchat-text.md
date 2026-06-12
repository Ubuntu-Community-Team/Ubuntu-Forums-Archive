---
title: "Cannot install xchat-text"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by joewhite on 2006-05-06
In Synaptic xchat-text wouldn't install so I downloaded the breezy package but got the same error message. It says I have the wrong version of xchat common installed. Any ideas?

Unpacking xchat-text (from xchat-text_2.4.4-0ubuntu5_i386.deb) ...
dpkg: dependency problems prevent configuration of xchat-text:
 xchat-text depends on xchat-common (= 2.4.4-0ubuntu5); however:
  Version of xchat-common on system is 2.6.0-0ubuntu1~breezy1.
dpkg: error processing xchat-text (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xchat-text

My sources.list says:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./
deb [http://theli.free.fr/packages/breezy/](http://theli.free.fr/packages/breezy/) ./

---

### Post by joewhite on 2006-05-06
Anyone?

---

