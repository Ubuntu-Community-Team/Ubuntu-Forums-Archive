---
title: "tar files"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by Nhatz on 2006-08-13
how do i extract tar files.... and the diff between .tar.gz and
.tar.bz2.... and how do i install them?
thanks!

---

### Post by Fass on 2006-08-13
You untar bz2 files with ```
tar xvjf file.tar.bz2
``` and gz files with ```
tar xvzf file.tar.gz
```. Gzip and Bzip2 are two different compression formats, some people like using one, some like the other (sort of like "zip" and "rar" in Windows).

You can learn more about "tar" by writing "man tar" in a terminal. You can do so about most commands - just enter "man [command]".

How you install the contents of the tar files depends on the contents themselves. Usually there is a readme file in the archive that tells you what to do.

---

### Post by LadyDoor on 2006-08-18
I've found it helpful to add some nice aliases to my .bashrc--you'll never have to type **tar -xvzf** again! If you want 'em, fire up your favorite text editor and add the following to the end of your .bashrc file.

```

alias untgz='tar -xvzf'
alias untbz='tar -xvjf'

```

Hope it helps!
--Door

---

### Post by 1FatCat on 2006-09-24
Newbie question:  <is tar a compression format similar in idea to zip or rar?  If so, do I need to download an additional program, or is it included in Breezy?

---

### Post by bodhi.zazen on 2006-09-24
Yers and included.

---

