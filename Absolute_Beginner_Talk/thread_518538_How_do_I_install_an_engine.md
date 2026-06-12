---
title: "How do I install an engine?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by bgissal on 2007-08-06
I am trying to install the rezlooks engine to complement the rezlooks Emerald theme I have just installed. Right now the .tar file is sitting on my desktop, but I don't know how to add it to the drop down box as a "Frame Engine" in Emerald. Any help????

---

### Post by Happy_Man on 2007-08-08
Well, extract the file to your Desktop, then open up a terminal and enter the following commands:

```
cd Desktop/<whatever the folder name is>
./configure
make
sudo make install
```

---

