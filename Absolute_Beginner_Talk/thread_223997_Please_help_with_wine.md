---
title: "Please help with wine"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by cac007 on 2006-07-27
I just installed wine.  I try to do winecfg and get this:



cory@ubuntu:~$ winecfg
wine: creating configuration directory '/home/cory/.wine'...

It will not go any further.  I've let it sit for 30 min.  Anyone have an idea of what is going on?

---

### Post by moma on 2006-07-27
Remove your wine
$ sudo apt-get remove --purge wine 

And re-install wine as instructed here
[http://ubuntuforums.org/showthread.php?p=1301662#post1301662]("http://ubuntuforums.org/showthread.php?p=1301662#post1301662")


// moma
   [http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")

---

### Post by cac007 on 2006-07-27
I did this and i am still getting the same thing

---

### Post by bullon on 2006-07-27
what happens if you right click on an .exe and choose "open with windows emulator"?

---

