---
title: "Creating Files in a directory"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by skrap on 2008-03-30
I  can seem to create a new profile in thunderbird.  Nothing I do will bring up the profile mgr
I can go to terminal and view the profiles I have 3 defaults.  The one I want is an empty directory and I want to copy files into this and make it the one profile.ini points to. Dont know how to copy the files from the dekstop.

---

### Post by Michael.Godawski on 2008-03-30
run in terminal
```
sudo cp /path/to/folder/or/file /path/to/new/location/
```
for copying many files from a directory run
```

sudo cp /path/to/folder/* /path/to/new/location/
```

---

### Post by skrap on 2008-04-01
Thanks Michael,

That was a huge help

---

