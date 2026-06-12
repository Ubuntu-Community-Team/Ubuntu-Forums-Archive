---
title: "How to detect which package owns some file?"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by Ilya Evseev on 2006-09-15
Wanted something like "pkg_which file" under FreeBSD or "rpm -qf file" under Redhat. Where to get the same functionality using dpkg and apt under Ubuntu?

---

### Post by Anonii on 2006-09-15
> **Ilya Evseev said:**
> Wanted something like "pkg_which file" under FreeBSD or "rpm -qf file" under Redhat. Where to get the same functionality using dpkg and apt under Ubuntu?
I'm quite sure you can do that from here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
"Search the contests of a package" will work, I guess.
There is probably a way throu the command line, which I unfortunately dont know, and I'd like to learn. So .. I'm waiting for a reply <:

---

### Post by 23meg on 2006-09-15
Use apt-file.

[http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-apt-file](http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html#s-apt-file)

---

### Post by mesilliac on 2008-01-28
This came up quite high in my google search results when I was trying to figure it out... in the end I remembered.

```
dpkg -S <filename>
dpkg --search <filename>
```

---

