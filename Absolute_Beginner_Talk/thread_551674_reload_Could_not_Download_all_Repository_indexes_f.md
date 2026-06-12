---
title: "reload Could not Download all Repository indexes feisty"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by GernBlansten on 2007-09-15
I am a complete newbie to linux and ubuntu. I running Feisty and when I launch Synaptic and hit reload, and wait, I get the following error. How can I fix this?

[B]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.[/B]

[I][http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg:) Could not resolve 'wine.lowvoice.nl'
[http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not resolve 'wine.lowvoice.nl'
[http://www.getautomatix.com/apt/dists/feisty/Release.gpg:](http://www.getautomatix.com/apt/dists/feisty/Release.gpg:) Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (216.120.255.9), connection timed out
[http://www.getautomatix.com/apt/dists/feisty/main/i18n/Translation-en_US.bz2:](http://www.getautomatix.com/apt/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (216.120.255.9), connection timed out
[http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz:) Could not resolve 'wine.lowvoice.nl'[/I]

Thanks for any help you can offer.

---

### Post by rsambuca on 2007-09-15
It looks like you have added some nonstandard repositories.  I do not know about the lowvoice ones, but I have been reading that the automatix servers have been down recently.  Perhaps just wait for a while to see if they get their servers back up.

---

### Post by GernBlansten on 2007-09-19
That was it. Thanks, I guess I got a little jumpy with the question.

---

