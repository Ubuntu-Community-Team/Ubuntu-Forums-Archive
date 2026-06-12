---
title: "How do I shred/erase the unused free space on my hard drive?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by ubacct3 on 2008-02-24
I think the "shred" command only does files.

---

### Post by oedha on 2008-02-24
mm.....are you talking about partition free space ? 
or
freeing your space up ?

---

### Post by oedha on 2008-02-24
for partition :=> you can use gparted [http://gparted.sourceforge.net](http://gparted.sourceforge.net)
for freeing up you space.....
sudo apt-get install autoremove
and
sudo apt-get autoclean

---

### Post by niteshifter on 2008-02-24
> I think the "shred" command only does files.

True, but for a regular file (not a device) shred "rounds up" the file size to the next full block (in the filesystem) and shreds that many blocks, in other words, shreds the slack space at the end of a file.

As far as a utility that iterates thru all the files in the filesystem wiping the slack space at the end of each - I don't know of such a tool in GNU/Linux. There was a tool called scrub that almost did that, but did so at the risk of locking the filesystem (consumed all available space).

---

### Post by ubacct3 on 2008-02-24
> **oedha said:**
> mm.....are you talking about partition free space ? 
or
freeing your space up ?

Hi, I'm looking to just delete the contents of the data that I've already emptied in the garbage.  I don't want any existing files to be modified at all.  I just want the free space to get wiped over with all zeroes.

Windows has a nice program called "Eraser" that does exactly that.

---

### Post by mbsullivan on 2008-02-24
Hey,

Check it out [here]("http://www.techthrob.com/tech/securedelete.php"). That should answer your question.

Mike

---

