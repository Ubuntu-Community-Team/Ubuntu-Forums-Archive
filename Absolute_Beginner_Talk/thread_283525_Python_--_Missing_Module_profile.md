---
title: "Python -- Missing Module profile"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by mesri on 2006-10-24
The distribution of Python 2.4.3 that came with Dapper doesn't seem to have the profile or pstats modules included -- I'm guessing this might be because potions of those modules are non-free.  Are there alternative modules around that would give the same functionality?  Or can someone just point me to the source code for these modules so I can install them myself?

---

### Post by jdong on 2006-10-24
python-profiler - deterministic profiling of any Python programs


The module is available in a separate package... use Synaptic to search for the package you need.

---

### Post by mesri on 2006-10-24
I did that already.  It doesn't seem to be there.

---

### Post by jdong on 2006-10-24
Hmm, are you positive? [http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=python2.4-profiler&version=dapper&arch=all](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=python2.4-profiler&version=dapper&arch=all) states that the profile and pstats modules are in the python2.4-profiler package.

---

### Post by mesri on 2006-10-24
python2.4-profiler doesn't show up in Synaptic.  (Neither does python2.3-profiler or python-profiler) I've searched for it manually and using the search box many times.

However, that link does lead me to the .deb for it, so I've installed that.  Thanks!

Any idea why I might not be seeing the package in Synaptic?

---

### Post by jdong on 2006-10-24
it's in multiverse... do you have the multiverse repository enabled?

---

### Post by mesri on 2006-10-25
Oops.  I thought I did, because I see Multiverse next to some of the section headings, but there aren't actually any packages in them.

Fixed now! :)  Thanks for your help.

---

