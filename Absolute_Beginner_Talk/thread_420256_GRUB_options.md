---
title: "GRUB options"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by thedevilisbad on 2007-04-23
how can I configure GRUB so Windows boots automatically instead of Ubuntu. I'm using a family PC and my parents aren't tech savvy and hate it when Ubuntu boots automatically.

---

### Post by crav on 2007-04-23
Along the same lines, how can I get rid of options in Grub? (I have older version of ubuntu i want to clear out)

---

### Post by indytim on 2007-04-23
The following should help you out.

[http://kubuntuforums.net/forums/index.php?topic=3081671.0]("http://kubuntuforums.net/forums/index.php?topic=3081671.0")

IndyTim

---

### Post by crav on 2007-04-23
Just to clarify, before I go and accidentally destroy grub; can I simply delete the options from menu.lst that I know longer need?

[http://paste.ubuntu-nl.org/17286/]("http://paste.ubuntu-nl.org/17286/")

Can i simply remove lines 12 through 36 and lines 50 through 59?

---

### Post by dreadlord_chris on 2007-04-23
> **crav said:**
> Just to clarify, before I go and accidentally destroy grub; can I simply delete the options from menu.lst that I know longer need?

[http://paste.ubuntu-nl.org/17286/]("http://paste.ubuntu-nl.org/17286/")

Can i simply remove lines 12 through 36 and lines 50 through 59?

There's no problem getting rid of those lines...

---

### Post by dreadlord_chris on 2007-04-23
> **thedevilisbad said:**
> how can I configure GRUB so Windows boots automatically instead of Ubuntu. I'm using a family PC and my parents aren't tech savvy and hate it when Ubuntu boots automatically.

Take a look at my reply in this thread:
[http://ubuntuforums.org/showthread.php?t=409771](http://ubuntuforums.org/showthread.php?t=409771)

---

### Post by indytim on 2007-04-23
Recommended:

1. Make a copy of your menu.lst
2.  Edit your mneu list and comment out the options you don't want.
3.  Save
4.  Re-boot
5.  If all is happy, go ahead and re-edit and delete the commented out lines


IndyTim

---

