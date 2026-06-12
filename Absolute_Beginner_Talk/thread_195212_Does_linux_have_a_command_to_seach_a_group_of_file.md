---
title: "Does linux have a command to seach a group of files for a text string?"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by jonboy99 on 2006-06-12
The title says it all really - if I have a folder full of text files, but can't remember which one contains a particular string of text, is there a way of finding which one without reading all the files by eye?

cheers
Jon

---

### Post by aysiu on 2006-06-12
Yes. ```
grep -inr *textyourelookingfor* /path/to/look/in
``` For example, if I'm looking for the phrase *chocolate* in the documents with my ~/recipes folder, I'd type ```
grep -inr chocolate ~/recipes
``` By the way, you asked specifically about a command. This can also be done graphically through the *gnome-search-tool*.

---

### Post by jonboy99 on 2006-06-12
cheers mate.  by the way, your website rawked when I first started with linux a few weeks ago, keep up the good work!  :D

---

### Post by aysiu on 2006-06-12
By the way, in case you're wondering what *-inr* is:

**-i** ignore case
**-n** display the line number of the matching line
**-r** search in subfolders, too

---

