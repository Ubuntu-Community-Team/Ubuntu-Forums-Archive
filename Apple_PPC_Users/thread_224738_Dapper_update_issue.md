---
title: "Dapper update issue"
date: 2006-07-28
forum: Apple PPC Users
---

### Post by kausbose on 2006-07-28
I got these three updates with my automatic update program for dapper.

kdelibs-bin 4:3.5.2-0ubuntu18
kdelibs-data 4:3.5.2-0ubuntu18
kdelibs4c2a 4:3.5.2-0ubuntu18

I tried to install them and I got this error.

E: /var/cache/apt/archives/kdelibs-data_4%3a3.5.2-0ubuntu18.1_all.deb: files list file for package `mozilla-mplayer' is missing final newline

If you could provide some insight how to work around this issue it would be helpful.

Thank you in advance

kausbose

---

### Post by rasec on 2006-07-28
Sometimes I get a similar problem to this on my debian box. One thing to try is to delete kdelibs-data_4%3a3.5.2-0ubuntu18.1_all.deb in your /var/cache/apt/archives/ directory. While your at it, you might want to delete mozilla-mplayer(something).deb in that same directory too and then try to do the update again. If that doesn't work than file a bug report at launchpad.

---

