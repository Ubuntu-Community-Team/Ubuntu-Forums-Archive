---
title: "Copying MASSIVE files [Resolved]"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Cullen on 2007-04-13
I am looking for a program similiar to Robocopy for windows.  Something that provides support for copying MASSIVE files and does so in a relatively swift manner, with an increased degree of stability (As compared to normal methods) and some sort of progress indicator.  Robocopy is command line driven, so that's cool but all I know of for linux is eith the "cp" command or just selecting and dragging the desired files.


PROBLEM SOVLED

---

### Post by raja on 2007-04-13
Have a look at rsync.
```
man rsync
```

---

### Post by Cullen on 2007-04-15
This is great, rysnc did exactly what I needed, however it didn't (or at least I couldn't figure how to make) provide any kind of progress indicators.  I did a breif google search and came up with Grsync, which is a GUI frontend for rsync.  Plugged it in to synaptic and boom it's beautiful.

---

### Post by raja on 2007-04-15
I didnt know about grsync.  Will check it out. Thanks.

---

