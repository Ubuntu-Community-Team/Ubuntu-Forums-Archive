---
title: "How do I make ISO?"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-06-19
I want to back up my home folder.  How do I make my home folder ISO?  Or better yet, just burn home directly into CD.

Can this be done in CLI?  If so, how?

---

### Post by aysiu on 2006-06-19
```
mkisofs -o homebackup.iso /home/tux101/
```

---

### Post by nalmeth on 2006-06-19
How big is your home folder? Bigger than 700 megs I'd have to imagine.

You can try a backup utility (I don't know of any, sorry) which will compress your files, possibly making them fit.

Got a DVD burner?

EDIT:
HA! good call aysiu!

---

