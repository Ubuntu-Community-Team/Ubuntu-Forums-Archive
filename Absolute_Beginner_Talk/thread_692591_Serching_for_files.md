---
title: "Serching for files"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by jbor7755 on 2008-02-09
This has to have a simple answer but, as a relative noob who wants to switch completely to linux, I'm rather unimpressed with Nautilus' ability to search for files.  Windows turns up all files with names containing the entered string but I cannot figure out nautilus' search algorithm.  I have yet to get the desired result after 6 months of use.

Any ideas on how to search for files?

This would be a really important feature for new users who may need to find documents from large packages (like latex for example) or the packages themselves.

Cheers

---

### Post by spiderbatdad on 2008-02-09
by default the search feature looks in the users home directory, since most files are stored in the filesystem, the desired result is usually obtained by selecting "look in: Filesystem"

---

### Post by anemptygun on 2008-02-09
> **jbor7755 said:**
> ...but I cannot figure out nautilus' search algorithm. 

What search algorithm did you use in windows?

---

### Post by asmoore82 on 2008-02-09
you could try `slocate` in a terminal,
but beware that its results are based on a filename database that is only updated once a day;
you can delete files and `slocate` will still show them there until the next update.

```
slocate *<filename_contains_search_text>*
```

---

### Post by asmoore82 on 2008-02-09
> **jbor7755 said:**
> This would be a really important feature for new users who may need to find documents from large packages (like latex for example) or the packages themselves.

Cheers

in Synaptic ("System -> Administration -> Synaptic Package Manager"),
click on the package to highlight it,
click "Properties," click the "Installed Files" Tab(3rd one for me).

---

### Post by rainwalker on 2008-02-09
I would recommend installing Beagle (packages are "beagle", "libbeagle0" and "python-beagle"
It only indexes your home directory, though.

---

### Post by asmoore82 on 2008-02-10
> **asmoore82 said:**
> in Synaptic ("System -> Administration -> Synaptic Package Manager"),
click on the package to highlight it,
click "Properties," click the "Installed Files" Tab(3rd one for me).

... Playing around with `xvidcap` ...

---

### Post by zvacet on 2008-02-10
If you want to search all filesystem then you have to be on top of it.Do it in terminal with cd / command.After that 

```
sudo find / -name *filename*
```

---

