---
title: "Search for files"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by counterpoint on 2007-04-18
It seems that "search for files" doesn't find all files if "File System" is chosen as the location.  I couldn't find a deeply nested "svn" file, although searching from /usr did find it.  Is that correct?  What limits the search, how can one know whether to expect all results to be found?

Also, how can the search be made more specific.  Typing "svn" as the search term returns everything that contains "svn".  How can you search just for files called "svn"?

---

### Post by Frederick J. Harris on 2007-04-18
with ya on that one counterpoint.  I've also found out the 'search' doesn't work like Windows.  I need to learn the difference too.

---

### Post by FuriousLettuce on 2007-04-18
You can do it from the command line - if you navigate to highest level that you want to begin your search (e.g. /  to search the entire system, /usr etc), then type 'find -name svn', that should return files simply called svn. You can use wildcards e.g., svn* or whatever. You might also want to check out Beagle - it carries out proper context-sensitive searches and is very quick once the indexing is done.

NB: To find files in restricted (non-readable folders), do sudo find -name myrestrictedfilename

---

### Post by zvacet on 2007-04-18
```
whereis file_name
```

---

