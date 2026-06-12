---
title: "Beginning bash command(s) problem."
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by dpneal on 2007-06-08
I'm trying to write a terminal command that will accomplish the following:

1) Look at the contents of a single directory, containing many dozens of smaller directories; and,
2) Delete every file matching a string within the many dozens of directories.

I've tried "rm -r *.m4p" within the master directory, but it can't find the contents of the sub-directories.


"ls -R Music/ *.m4p" prints out all of the contents of all subdirectories of Music, where I'm only looking for m4p files.

grep seems to be examining the contents of the files themselves; I can't figure out how to get grep to only examine the filenames.

I'm at a bit of a loss.  My thought process was (a) apply a recursive filter looking for *.m4p files, then (b) pipe the output of that recursive filter into an rm command somehow.

Thanks for any feedback!

(In case anyone is curious, I'm migrating from XP with iTunes to Linux with ... amaroK)

---

### Post by yurimxpxman on 2007-06-08
> **dpneal said:**
> I'm trying to write a terminal command that will accomplish the following:

1) Look at the contents of a single directory, containing many dozens of smaller directories; and,
2) Delete every file matching a string within the many dozens of directories.

I've tried "rm -r *.m4p" within the master directory, but it can't find the contents of the sub-directories.


"ls -R Music/ *.m4p" prints out all of the contents of all subdirectories of Music, where I'm only looking for m4p files.

grep seems to be examining the contents of the files themselves; I can't figure out how to get grep to only examine the filenames.

I'm at a bit of a loss.  My thought process was (a) apply a recursive filter looking for *.m4p files, then (b) pipe the output of that recursive filter into an rm command somehow.

Thanks for any feedback!

(In case anyone is curious, I'm migrating from XP with iTunes to Linux with ... amaroK)
Change **rm -r *.m4p** to [b]rm -R *.m4p[b].

---

### Post by jyba on 2007-06-09
I'd do it like this...
```
find Music -name *.m4p -delete
```

---

### Post by dpneal on 2007-06-09
Perfect, thanks!

---

