---
title: "help with deleting and space reduction"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by insub2 on 2006-09-01
ubuntu wont let me log in because my partion is full.  i was trying out stuff with compresstion of archives and whatnot and filled up my / partition.  i deleted the file but my partition is still full.  how can i free up space using ubuntu live or knoppix.  AND how do i really delete things (for future use).

---

### Post by Metacarpal on 2006-09-01
If you're deleting files while logged in as root or somesuch, you'll have to (while in on the acct you used to delete the files) look for a hidden .trash folder in that partition (hit Ctrl+h in Nautilus to show hidden files) and empty it.  Then you'll have free space.

---

### Post by insub2 on 2006-09-01
thanks!!!

that worked except when i deleted it, my archive file got put into "/.trash-root". no big, just had to delete it from there too.  and now my computer works againg:mrgreen: :-D :biggrin:

---

### Post by Metacarpal on 2006-09-02
Yay!  Glad I could help.  I ran into the disk full problem with a USB thumb drive.  If you use one of those, watch for the .trash folder on deletion of files.

---

