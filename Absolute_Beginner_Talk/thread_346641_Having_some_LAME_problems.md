---
title: "Having some LAME problems"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by wickstopher on 2007-01-26
Hello!  I am having troubles locating the file libmp3lame.so.

I have taken the following steps:

- sudo apt-get install lame (it told me that I already had the most recent version of LAME installed)
-followed the "Enabling Extra Repositories" tutorial at [http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")
-through Synaptic, installed liblame0 and liblame-dev

and I still don't have this file in my /lib, or (as per searching my file system and as far as I can tell) anywhere else for that matter!  Any help would be greatly appreciated.

---

### Post by po0f on 2007-01-26
wickstopher,

The file is in /usr/lib.

---

### Post by wickstopher on 2007-01-26
Just checked, once again, and it's not there!  Any ideas?

---

### Post by Iarwain ben-adar on 2007-01-26
It is there,

Try this
```
sudo slocate -u
```(this will update your search dir's)

and then ```
locate libmp3
```

It works here..


Iarwain

---

### Post by wickstopher on 2007-01-26
It is there.  When I was looking in that same directory earlier, it didn't show up.  Why is that? (That is, if you care to enlighten...if not, you have already done me plenty of good).  Thanks for the (very timely) help.

---

