---
title: "Repositories"
date: 2005-09-08
forum: Absolute Beginner Talk
---

### Post by jbinc1 on 2005-09-08
Hello,

Can someone help me with the latest repositories for digikam? I added these from a link on the digikam web site  to my source.list file 
( deb [http://www.mpe.mpg.de/~ach/kubuntu/hoary](http://www.mpe.mpg.de/~ach/kubuntu/hoary) ./ and deb-src [http://www.mpe.mpg.de/~ach/kubuntu/hoary](http://www.mpe.mpg.de/~ach/kubuntu/hoary) ./ ). Synaptic scans them but I don't seem to be getting the latest release. If I go to the repository site, it shows 0.7.4-0 as the latest but synaptic shows 0.7.3. If I try to install any of the new packages, I get an error saying, " software cannot be authenticated." I'm trying to get the latest digikam and the kipi-plugins. Does anyone have a clue what I'm doing wrong?

---

### Post by Steve1961 on 2005-09-09
Be careful adding software from new repositories as they can sometimes break your system.  If you can already see a version of the package you need in synaptic, which doesn't look too old, I would recommend installing that.  You may still get the software cannot be authenticated message if you're using the universe or multiverse repositories, but if you press OK you can still install

---

### Post by jbinc1 on 2005-09-09
Thanks for the reply. Does it still have a chance to break my system even if it's the repositories that digikam links to? The other repositories don't offer the kipi-plugins I'm looking for so I can create dvd slideshows in digikam.

---

### Post by Steve1961 on 2005-09-09
I suppose the simple answer is that anything could potentially break your system so in the end it's up to you.  That said, I install packages from the universe, multiverse and backports repositories all the time and haven't had any problems.

---

### Post by poofyhairguy on 2005-09-09
[QUOTE=jbinc1]Hello,

Can someone help me with the latest repositories for digikam? I added these from a link on the digikam web site  to my source.list file 
( deb [http://www.mpe.mpg.de/~ach/kubuntu/hoary](http://www.mpe.mpg.de/~ach/kubuntu/hoary) ./ and deb-src [http://www.mpe.mpg.de/~ach/kubuntu/hoary](http://www.mpe.mpg.de/~ach/kubuntu/hoary) ./ ). Synaptic scans them but I don't seem to be getting the latest release. If I go to the repository site, it shows 0.7.4-0 as the latest but synaptic shows 0.7.3. If I try to install any of the new packages, I get an error saying, " software cannot be authenticated." I'm trying to get the latest digikam and the kipi-plugins. Does anyone have a clue what I'm doing wrong?[/QUOTE]

I can tell you from experiance: it didn't work for me.

---

### Post by jbinc1 on 2005-09-10
Would it be better to compile from source?

---

### Post by jbinc1 on 2005-09-13
I solved my own problem. At least for now. I have been using apt-get instead of synaptic or kynaptic and I was able to get the latest digikam and it's support apps.

---

