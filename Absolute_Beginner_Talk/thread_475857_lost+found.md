---
title: "lost+found"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by scradock on 2007-06-16
Would anybody like to enlighten me and other beginners about the "lost+found" folders?

What are they for; can I use them; who else uses them; and so on? 

Can I manage without some of all of them? (one per partition, as far as I can see -

---

### Post by floke on 2007-06-16
I think its a dumping ground for the ext3 journaling system in case of a crash. Anything that can't be recovered gets left there for your perusal.

At least I think that's what its for!

---

### Post by Blario on 2007-08-12
I was shrinking my storage ext3 partition with gparted when I continued to fail for some reason...
End result - all my storage ended up in lost+found.

I'd like to know what's the best/recommended/designated way of recovering files out of lost+found.  Aren't they put there to mean they're of some use?

---

### Post by Jimmyfj on 2007-08-12
lost+found is the place where corrupted files are placed when they are found during a filesystem check.

[http://www.openaddict.com/documents/Linux-Filesystem-Hierarchy/lostfound.html](http://www.openaddict.com/documents/Linux-Filesystem-Hierarchy/lostfound.html)

I just did a google search - Wanted to know myself too what the folder are for :)

---

