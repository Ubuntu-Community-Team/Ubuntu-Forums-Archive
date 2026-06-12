---
title: "Check install size"
date: 2008-07-31
forum: Arch and derivatives
---

### Post by YodaMstr on 2008-07-31
Hey all, I was wondering if there's an easy way to check how much the "base" installation size is on a comp.  The only way I can think is to find out how much my desktop/media folder takes up, and then subtract it from the "space used" output on the GNOME system terminal.  I'm not entirely sure how accurate that is.

---

### Post by tuxxy on 2008-07-31
In terminal try

```
 df -kh

```

---

### Post by YodaMstr on 2008-07-31
I didn't know about the df command, and I was wondering if there was one that did such as that, thanks.  However, this shows me the total space used on my hard drive.  I was wondering if there was a way to deduce the size of all installed applications, and the base of Arch.  i.e. a way to see the total size of an installation sans personal files, such as movies and music.

---

### Post by B-Con on 2008-08-01
Is all your media stuff on other file systems mounted on /media? If so, df only reports statistics on the file system level, so each mounted file system is separate. You'll be interested in what your / usage is. Subtract from it the total size of your home directory (which is more accurate than just your Desktop). You can get the size of that by going to /home and right-clicking your directory and getting the file size of it.

---

