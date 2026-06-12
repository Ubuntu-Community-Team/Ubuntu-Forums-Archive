---
title: "check disk in terminal"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by bigal1932flying on 2007-06-20
What is the exact syntax to start check disk from terminal.

---

### Post by ryanVickers on 2007-06-20
sudo fsck /dev/<devicename>

mack sure the filesystem is unmounted however!!  It will explain further if you try it mounted...

---

### Post by arvevans on 2007-06-20
In terminal mode, type "man fsck".  The resultant manual page will tell you all about it.
When viewing man pages you have to use arrow keys to scroll up & down and hit a "q" to exit.
_._

---

### Post by JebusWankel on 2007-06-20
I believe > man fsck should do the job.

Oops, guess I'm a little slow.

---

### Post by ryanVickers on 2007-06-20
Infernal experts and their fancy manuals and such! :p

---

