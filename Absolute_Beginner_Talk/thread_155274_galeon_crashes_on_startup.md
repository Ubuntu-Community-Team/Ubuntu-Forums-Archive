---
title: "galeon crashes on startup"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-04-04
This problem has been posted previously, but not being answered since. Since I've had the same problem, and couldn't find a solution even on the gnome forums, I bother thy with this trivial question:

How is it possible, that galeon crashes on startup, giving the following error message if started from a terminal:

In the case of the previous post:

sh4ka@machine:~$ galeon
INTERNAL ERROR on Browser End: JavaPluginFactory5 init - no agent?
System error?:: File or directory doesn't exists


In my case:

niko@obenlinks:~$ galeon

** (galeon:9333): WARNING **: I could not load the bookmarks file, will load the default bookmarks from /usr/share/galeon/default-bookmarks.xbel.
INTERNAL ERROR on Browser End: JavaPluginFactory5 init - no agent?

System error?:: No such file or directory


I don't have a clue what this means. Thanks

---

### Post by catlett on 2006-04-04
It appears this is a known bug. If you want to research and solve it, it appears these guys have a work around for it. Plus there is a link on this page to thew Mozilla bug report. [https://launchpad.net/distros/ubuntu/+source/galeon/+bug/3747](https://launchpad.net/distros/ubuntu/+source/galeon/+bug/3747)

---

