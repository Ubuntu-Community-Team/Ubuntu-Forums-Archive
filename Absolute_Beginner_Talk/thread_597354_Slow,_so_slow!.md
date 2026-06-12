---
title: "Slow, so slow!"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by urrybr on 2007-10-30
I am using Ubuntu to run the B.R.U. backup software, with an Overland NEO 4000 tape library.  Last week we had a major crash and I had to reinstall Ubuntu, and BRU softwares.  Since that time Ubuntu has been somewhat slower--it is especially noticeable when I use the Terminal at the full-screen setting.  The biggest problem that we are encountering is that when our BRU app begins to verify the tape that has just been written, it takes serveral hours, rather than the 30 to 40 minutes that it used to take.  Where can I go to tune up my Ubuntu installation so that it will perform better?  I am running 6.06 LTS.

---

### Post by Crafty Kisses on 2007-10-30
> **urrybr said:**
> I am using Ubuntu to run the B.R.U. backup software, with an Overland NEO 4000 tape library.  Last week we had a major crash and I had to reinstall Ubuntu, and BRU softwares.  Since that time Ubuntu has been somewhat slower--it is especially noticeable when I use the Terminal at the full-screen setting.  The biggest problem that we are encountering is that when our BRU app begins to verify the tape that has just been written, it takes serveral hours, rather than the 30 to 40 minutes that it used to take.  Where can I go to tune up my Ubuntu installation so that it will perform better?  I am running 6.06 LTS.

Hmmm, try the following command:
```
top
```
See if anything is using up a lot of resources.

---

