---
title: "Aargh! Can't update! (Solved)"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by editrix on 2005-10-19
Just spent 13 hours (overnight) updating using the red button by the clock.  Now I'm told: 

E: /var/cache/apt/archives/dpkg_1.10.27ubuntu2_i386.deb:  cannot access archive: No such file or directory

And the red button is still lit, and clicking it calls up the update program, which has *everything* still checked, as if nothing's been updated!

On Ubuntu 5.04

Now what?

---

### Post by Gustav on 2005-10-19
Try using

sudo apt-get update

in the terminal. That might give you more information.

---

### Post by editrix on 2005-10-19
Hi Gustav. Wow, no matter how GUI it gets, you still need the terminal. I should have a big picture of one hanging on my wall :-)

You were quite right. When I did the update, it Fetched 34.1kB of files. Everything else was the mirrormax thingy. So I guess I'm updated. Thanks.

---

