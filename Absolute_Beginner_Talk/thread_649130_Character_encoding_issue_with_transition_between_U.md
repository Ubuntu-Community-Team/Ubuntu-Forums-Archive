---
title: "Character encoding issue with transition between Ubuntu and WinXP."
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by renaudb on 2007-12-24
Hi,

I need help on how to resolve this problem. I have both WinXP and Ubuntu on the same computer, and they both mount an Ext2 partition (Windows loads it using IFS Driver). The problem is that I named many files on this partition with French accented characters like "é", "ç", etc, under Ubuntu (so using UTF-8 encoding). Now when I browse these files, I see weird characters under Windows in their filenames, and most of the time I cannot open them by double-clicking on them, and sometimes programs crashes using them.

I know that from now on I will not use special characters in my filenames, but I already have a lot of filenames to change and it would be way too long to do so manually under Ubuntu. I need some suggestions on how to do that, either under WinXP or Ubuntu, it doesn't matter to me. I already explored some solutions, like the "rename" console command, but I really cannot get over the PerlRegExpr part. I heard of a program called "convmv", but it didn't work out for me. There are batch renaming programs under Windows, but they cannot understand UTF-8 characters. I'm not saying I've tried everything, it's just that I haven't succeeded in any ways yet!

In summary, what I would like to do would be to replace these accented characters with normal letters (like "é" by "e", "ç" by "c", ...). Either by using commands or by converting the whole encoding of the partition to something readable under WinXP.

Thanks a lot for your help!

---

### Post by erginemr on 2007-12-24
There is a good KDE app for batch renaming (There is one for Gnome as well, but I don't remember its name). Its home page is:
[http://www.krename.net/](http://www.krename.net/)

You can install it with:
```
sudo aptitude install krename
```
and when you are done, remove it (together with all its KDE dependencies with:
```
sudo aptitude remove krename
```

---

