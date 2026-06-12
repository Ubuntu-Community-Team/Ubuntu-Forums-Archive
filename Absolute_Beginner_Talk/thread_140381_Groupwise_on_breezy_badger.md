---
title: "Groupwise on breezy badger"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by ndajee on 2006-03-06
Help. !! I am dual booting with XP and on the Ubuntu side I need to run Groupwise and the client, not web based. I used alien to convert from .rpm to .deb, with no errors, I installed groupwise with no errors, but when I try to run the groupwise executable, nothing happens, can someone help please?

---

### Post by Sweet on 2006-03-06
When you try running it from the terminal what output do you get?

---

### Post by ndajee on 2006-03-06
./ groupwise error while loading shared libraries: libstdc++.so.5. Cannot open shared object file, no such file or directory. 

When I do a search for libstdc++.so.5 then synaptic lists it on the left hand pane, but I do not know how to install it. It does not allow me to install

---

### Post by Sweet on 2006-03-06
Search synaptic for "libstdc++" and check the box next to "libstdc++5" for example.

You may need to add extra repositories if the search doesnt yield any results.

Might be of use if you need to add repos:
[http://ubuntuforums.org/showthread.php?t=92672](http://ubuntuforums.org/showthread.php?t=92672)

---

