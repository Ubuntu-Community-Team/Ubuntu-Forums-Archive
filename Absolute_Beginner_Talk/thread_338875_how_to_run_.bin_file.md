---
title: "how to run .bin file?"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by ajmorris on 2007-01-15
I have a .bin file (called "lg3d--1-0-0-linux-i686-0612190943.bin") that i want to install. How do i do this? It is lg3d (Looking Glass) there were ubuntu repositories but they didn't work.

---

### Post by jordanmthomas on 2007-01-15
cd to the directory it is in (assuming on your desktop)
```
cd ~/Desktop
chmod +x lg3d--1-0-0-linux-i686-0612190943.bin  #  make it executable
sudo ./lg3d--1-0-0-linux-i686-0612190943.bin #  maybe sudo isn't necessary -- not sure where it installs

```

alternatively, you could right click on it and go to properties and then make it executable that way and you would just need to double click it to run it.  The downside here is if it needs root privileges the execution will fail

**edit  :  Oh, and project looking glass sucks and is a pain to get working sometimes, but good luck!

---

### Post by ajmorris on 2007-01-15
thanks i tried that and didn't work. But i just figured it out it is sh./lg3d.....bin.
:)

---

### Post by jordanmthomas on 2007-01-15
Well, it will work for most bin files.
You'd think they could have added one line to it to make it the same as every other bin file I have ever seen
```
#!/bin/bash
```
...jerks  :)

---

