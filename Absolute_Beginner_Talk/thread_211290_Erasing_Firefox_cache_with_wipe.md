---
title: "Erasing Firefox cache with wipe"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by jason1 on 2006-07-08
I just installed Ubuntu 6.06 after a year or so with Novell 9.  I like it!  But, I have a query concerning privacy:

I have configured Firefox to empty the cache after each session.

I also downloaded (via synaptic) the "wipe" hard drive shredder program.

What I want to be able to do is this:

After closing down Firefox, I want to know the name of the partition where the cache is placed.

Then, I want to know what command to type into the wipe program in terminal, so that the file names and sites that I have been browsing will be shredded in a cycle of 7 wipes (DOD standard).

In Novell 9, I was using BCwipe and just shredding the whole dev/shm/, but I would like to know if there is a better way, or if that was even correct.

Thank you in advance.

---

### Post by Rich3077 on 2006-07-08
Sorry I dont know the answer to your question, but am replying because I would like to know as well!

---

### Post by paxmark1 on 2008-03-15
I have a script for it in opera  I named it operacache and put it in ~/bin and made executable

#!/bin/bash

cd ~/.opera/cache4
wipe -qr o*


I went looking how to do it in Firefox and only found your unanwered reply.

peace

---

### Post by Oldsoldier2003 on 2008-03-15
> **jason1 said:**
> I just installed Ubuntu 6.06 after a year or so with Novell 9.  I like it!  But, I have a query concerning privacy:

I have configured Firefox to empty the cache after each session.

I also downloaded (via synaptic) the "wipe" hard drive shredder program.

What I want to be able to do is this:

After closing down Firefox, I want to know the name of the partition where the cache is placed.

Then, I want to know what command to type into the wipe program in terminal, so that the file names and sites that I have been browsing will be shredded in a cycle of 7 wipes (DOD standard).

In Novell 9, I was using BCwipe and just shredding the whole dev/shm/, but I would like to know if there is a better way, or if that was even correct.

Thank you in advance.

look in your home directory. the cache is in a hidden folder, mine is :
/home/me/.mozilla/firefox/am86agg3.default/Cache
not sure if the am86agg3.default is randomly generated but you get the general idea :)

---

### Post by the-edmeister on 2008-03-15
Type **about:cache** in the Firefox URL bar and hit Enter.
The location should be there under Disk Cache Device > Disk Cache Directory

---

### Post by The Seeker on 2008-03-15
> **jason1 said:**
> I also downloaded (via synaptic) the "wipe" hard drive shredder program.

Why not just use shred?

```
$ shred -z -u -v foo
```

---

