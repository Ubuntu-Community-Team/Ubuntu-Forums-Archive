---
title: "Searching"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by micrologix on 2006-03-30
I am new to LInux and would like to know how to search for a file within all directories, like doing a search of your C drive in windows, thanks.

---

### Post by yota on 2006-03-30
Hi,

you can use "Search files" under the "places" menu or "locate" and "find" from the command line (type "man *command*" to have help).

Have a look at [http://ubuntuforums.org/showthread.php?t=142716](http://ubuntuforums.org/showthread.php?t=142716) for some usefull infos.

---

### Post by micrologix on 2006-03-30
Thanks, perhaps I should have looked a little further before jumping to questions, just eager to get cracking with it I suppose :-)

---

### Post by wout.wepsait.com on 2006-03-30
[quote=micrologix]Thanks, perhaps I should have looked a little further before jumping to questions, just eager to get cracking with it I suppose :-)[/quote]

Ask all your questions that way we know what the communities problems are. So in this case, thanks for your input.

---

### Post by johnnymac on 2006-03-30
If you'd like to do it from a command line......

```

cd /
find -name <part or all name of file> -print

```

That will search through all your directories and find the file for you and print out where it's located......

---

