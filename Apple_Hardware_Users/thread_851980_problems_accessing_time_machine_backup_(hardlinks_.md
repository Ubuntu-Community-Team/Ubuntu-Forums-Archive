---
title: "problems accessing time machine backup (hardlinks on HFS+?)"
date: 2008-07-07
forum: Apple Hardware Users
---

### Post by the_laws_of_physics on 2008-07-07
My mac died so I'm now on Ubuntu. All my data is on a "time machine" backup. I can mount and access the drive from Ubuntu, but all directories show up as files. I already googled and found out that Linux isn't able to interpret them as hardlinks. (thanks to Steve Jobs for selling all this proprietary stuff)

Is there any module/program whatever that allows to access a time machine backup correctly (read-only would be sufficient)?

Is there any other way to extract data from a "time machine" backup?

---

### Post by DonnieP on 2008-07-07
> **the_laws_of_physics said:**
> My mac died so I'm now on Ubuntu. All my data is on a "time machine" backup. I can mount and access the drive from Ubuntu, but all directories show up as files. I already googled and found out that Linux isn't able to interpret them as hardlinks. (thanks to Steve Jobs for selling all this proprietary stuff)

Is there any module/program whatever that allows to access a time machine backup correctly (read-only would be sufficient)?

Is there any other way to extract data from a "time machine" backup?
Don't know about a program, but I do see that the backed up files are in a dot directory (if you're using Nautilus, choose the option to see hidden files):  .HFS+ Private Directory Data.  It's not real useful since there's thousands of directories underneath this dot directory (one for everytime TimeMachine took a look, I suppose), but there are real backed up files in those subdirectories.

---

### Post by the_laws_of_physics on 2008-07-08
even in this hidden directory most files show up as hardlinks. Some are real files though. The problem is: I have about 20,000 directories there! :confused:

---

### Post by cyberdork33 on 2008-07-08
Your best course of action would be to use a mac to mount the sparseimage and get your files out that way...

---

