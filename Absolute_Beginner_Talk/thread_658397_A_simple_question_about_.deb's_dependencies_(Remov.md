---
title: "A simple question about .deb's dependencies (Removing)"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2008-01-04
If I install some deb package that needed a dependency, and then I remove that package using synaptic, as far as I know that installed dependency remains on my system.

How can I install deb's making sure that once uninstalled everything that's not needed will be removed? 


Thank you

---

### Post by dannyboy79 on 2008-01-04
well, I use aptitude instead of apt-get. Aptitude is suppose to do what you're asking about, remove any dependencies that were installed with that app and are no longer needed. there's got to be some command which can be run to find unneeded dependencies but I am unaware of what it is. You're talking about such a small amount of space however. Libraries and dependencies are very tiny in size. Are you short on space?

here's some info that'll be helpful: [http://www.debian.org/doc/FAQ/ch-pkgtools.en.html](http://www.debian.org/doc/FAQ/ch-pkgtools.en.html)

---

### Post by p_quarles on 2008-01-04
apt-get will mimic aptitude's default behavior if you add the "--auto-remove" option. 
```
sudo apt-get remove --auto-remove *packagename*
```
And, yes, you can remove .deb packages use APT.

---

### Post by kellemes on 2008-01-04
Instead of Apt-get use aptitude to install packages so you can remove them including dependencies.
[https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide)
[http://nixdoc.net/man-pages/Linux/aptitude.1.html](http://nixdoc.net/man-pages/Linux/aptitude.1.html)

You may need "apt-get install aptitude" first. :)

---

### Post by kellemes on 2008-01-04
> **dannyboy79 said:**
> there's got to be some command which can be run to find unneeded dependencies but I am unaware of what it is.

aptitude clean --purge-unused

---

### Post by Kosimo on 2008-01-04
Thanks all for answering.
No, I'm not running low on space. Is just a matter of not creating a mass on my system. I use to install some deb's I download from some trusted sites. And I use to install them using the GUI that Gutsy easily gives me. 

So, using that way I'm assuming that it doesn't record any dependency or anything else. So when removed that dependency will remain on my system.  As said looks like those dependencies are small. But the question is, why should I keep them if I really don't need them anymore? 
Just for a matter of efficiency.

Installing that package using aptitude should help me to completely remove it from synaptic? 

Sorry guys but I prefer to not use command line if possible.

Thank you again.

---

### Post by kellemes on 2008-01-04
Just typing aptitude gives you a fine gui.

---

### Post by rharris on 2008-01-04
Have a look at gtkorphan. Its in the repos.

Rob

---

### Post by Paqman on 2008-01-04
[HowTo: Cleaning up all those unnecessary junk files...](http://ubuntuforums.org/showthread.php?t=140920)

---

