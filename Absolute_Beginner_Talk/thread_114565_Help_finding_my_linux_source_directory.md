---
title: "Help finding my linux source directory"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by Solhan on 2006-01-08
I recently had a more knowledgable person install 5.10 GNOME Ubuntu, out of fear that I may not do it correctly.  Now, I've gotten my hands on a wireless network card from a friend, and downloaded the drivers.  When I run the configure, it asks for the linux source directory, and I don't know where that is.  I tried the default of /usr/src/linux and its not there.  I was curious if someone could name a file in that directory that I could search for and thus find the directory.  Thanks!

---

### Post by towsonu2003 on 2006-01-08
put in your ubuntu install cd (or don't, if you have internet connection) and ```
sudo apt-get update
sudo apt-get install build-essentials
```

then it should be able to find the source...

---

