---
title: "Speed up booting on legacy laptop?"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Old Pink on 2007-07-23
Any ideas, please? :) 

All this laptop is for is browsing and pidgin, really, so alot could go. :)

FYI, Laptop model is [Dell Latitude L400]("http://www.mbhoy.com/21-07-2007/dell-latitude-l400-laptop")

---

### Post by weijie90 on 2007-07-23
get rid of stuff like bluetooth, hplip printing and cups.

---

### Post by Old Pink on 2007-07-23
Already done.

Here's a bootchart:

---

### Post by MrHippocampus on 2007-07-23
You could try profiling your boot, this is where the system remembers which files are loaded at boot time and remembers to preload them the next time the system is booted.

Its not too hard to do either, when grub appears, edit the ubuntu line which you normally boot, and then edit the top line of that, simply add the word "profile" on the end. The system will boot a lot slower this time round, but subsequent boots should be faster.

---

### Post by sailor2001 on 2007-07-23
also you can go  sudo gedit /boot/grub/menu.lst  and set your time up to immediate vs 10 sec or what ever it is listed at

---

