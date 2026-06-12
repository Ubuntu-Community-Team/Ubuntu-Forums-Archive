---
title: "64 bit gutsy tar gz file unpacking  problems"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by thuds on 2007-12-10
im having a strange problem, any time i try to "unpack" a tar gz file, it fails and then gives me about a hundred repeating errors

tar: avant-window-navigator-0.1.1/mkinstalldirs: Cannot utime: Operation not permitted
 
that look like that. i would really like to know how i might fix this problem so that i can install things other than that which is allowed by add/remove programs.
i thought it might just be a bad file but this is the third file in a row that doesnt work. all help would be appreciated

---

### Post by p_quarles on 2007-12-11
It sounds like a permissions problem. It also sounds like the .tar.gz file is trying to unpack into a directory that it doesn't have permission to create, which seems odd.

Anyway, I've got a couple questions:
1) What program are you using to unpack the file? The command line? The graphical file manager?
2) Can you post a link to where you got this file, so that I or someone else can doublecheck it?

---

