---
title: "Another strange result - file search"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by RogerDavis on 2007-05-06
Using file browser, I'm trying to search out all files on the entire hard drive of a certain name or containing a word or phrase.  

But when I enter it, all the files aren't found.  I'm following the instructions in help EXACTLY.  

It seems (maybe?) that it's not looking at the entire hard drive.  I'm not restricting the search in any way that I can discern.

How can I make it search everywhere and find all files?  Or will it simply not do this?

Also, it doesn't show me where the few files it will find are located.  How do I display this?

---

### Post by AtrejuT on 2007-05-06
are you using beagle to search? it usually only indexes your home directory but also find the search string in the content of various files etc.
the (i think) easiest way to find files by filename is to open a terminal and enter
```

slocate searchstring

```

but I don't know if that's what you are looking for?

---

### Post by annda on 2007-05-06
i can't help you with adjusting nautilus search (it searches YOUR files be default, i.e. basically your home directory). but you  can use a command line:

```
sudo updatedb
```

will update the index of all files on your system. then you can use this to find files including the search term in their names:
```

locate some_name
```

if you want to search WITHIN files, the grep command is useful. but there are good GUI tools too: beagle and tracker.

---

### Post by RogerDavis on 2007-05-06
1) What's Beagle?  What's Tracker?  What's the difference?

2) The terminal commands work, but I much prefer a graphics interface for so many files.

3) Are there other graphically based options?

---

### Post by dwblas on 2007-05-06
If you have MC (Midnight Commander) installed, it is F9, Command, Find File.

---

### Post by annda on 2007-05-06
beagle is known to hog system resources. tracker is more user-friendly that way.

you can install tracker by:

sudo apt-get install tracker tracker-search-tool

more info here:
[http://www.gnome.org/projects/tracker/](http://www.gnome.org/projects/tracker/)

---

