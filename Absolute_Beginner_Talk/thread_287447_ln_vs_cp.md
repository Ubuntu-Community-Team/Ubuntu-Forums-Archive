---
title: "ln vs cp?"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Kurt` on 2006-10-28
Hi,

I've always wondered... what's the point of creating a "hard link" when you can just create a copy of the file?

ln file1 file2

vs.

cp file1 file2

Can anyone clear this up for me?

Thanks!

---

### Post by PriceChild on 2006-10-28
Because you can just edit the one file.... and it is updated in both places.

For example... if many programs need one library to function.... why give each program its own library when you can use a central source which they all go to?

---

### Post by fritz_monroe on 2006-10-28
If you make a copy of the file, you have just that, 2 copies of the file.  But what if you make a change to the original file?  You then have to make that same change to the copy.

If you make a link, then you change the original file and access to that file from those links is changed as well.

---

### Post by aysiu on 2006-10-28
I think the better question is the reverse--why copy a file, when you can create a link to it?

Takes up less space, updates "both" (which are really just the same file referenced in two different places).

---

### Post by Kurt` on 2006-10-29
Then why are there "hard" links AND "soft" links?

If **ln -s file1 file2** and **ln file1 file2** will both create a link to file 1, what's the difference?

---

### Post by Bachstelze on 2006-10-29
A "soft" or "symbolic" link is a file which links to another while a "hard" link is just two names for the same file.

The main difference is tat hardlinks cannot "cross" filesystems (that is, you can create on a given partition a hardlink to a file located on another).ndows

---

### Post by Kurt` on 2006-10-29
I've been using symlinks for quite a while, and I recently wondered what happens when you don't use the -s switch. ;)

Now I know, thanks everyone. :D

---

