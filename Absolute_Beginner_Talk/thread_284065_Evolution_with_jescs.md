---
title: "Evolution with jescs"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by herskegut on 2006-10-25
Goodmorning everybody :-)

i am more or less new to ubuntu, but have worked with Solaris the past 3 years.
Now, i have a serious problem.. i want to use jescs (Java enterprise system Calendar Server), to connect up to the calendar at work and sync it.
After installing evolution-jescs, (and belive me, it was a buggy :-P ) i had an option in evolution called "JESCS" and i was all \\:D/
Until i tried to get it to work :-(
i follow this guide, [http://www.go-evolution.org/index.php?title=Evolution_JESCS&redirect=no](http://www.go-evolution.org/index.php?title=Evolution_JESCS&redirect=no)
But i can't select my mail server to be a Sun Calendar WCAP server, anyone have an idear ? :-)

---

### Post by martti on 2007-01-29
Ok, I had similar problem with the 2.8.0-0ubuntu1 version of the evolution-jescs package. I resolved the problem the following way:

$ sudo ln -s /usr/lib/evolution-data-server-1.2/camel-providers-9/libcamelsunone.so \
/usr/lib/evolution-data-server-1.2/camel-providers-8/

$ sudo ln -s /usr/lib/evolution-data-server-1.2/camel-providers-9/libcamelsunone.urls \
/usr/lib/evolution-data-server-1.2/camel-providers-8/

After that, WCAP protocol appears in the list of available protocols exactly as illustrated at [http://www.go-evolution.org/index.php?title=Evolution_JESCS&redirect=no](http://www.go-evolution.org/index.php?title=Evolution_JESCS&redirect=no).

---

