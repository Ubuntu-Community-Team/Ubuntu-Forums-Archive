---
title: "having trouble installing kde window decorations"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by qiemem on 2007-06-14
I was running xubuntu and decided I wanted to give kde another try. So I installed kde-core (this is sort of a lighter weight laptop, so I didn't want the full blown kubuntu) and its running great except that whenever I try to install a new window decoration, I get:
```
checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!
```
off the ./configure. Anyone what's up? (oh, and it won't let me make after that)

---

### Post by Clay_Banger on 2007-06-14
try installing it from the repos instead of the source code.

make sure you have the [extra repos enabled]("http://www.psychocats.net/ubuntu/sources") and then type this into the terminal:
```
sudo aptitude install kde-core
```

---

### Post by qiemem on 2007-06-15
Oh, kde-core is installed from the repos. Its the window decorations that I'm installing from source. Oh, well I guess I should ask, are there any kde window decoration packages in the repos?

---

### Post by Clay_Banger on 2007-06-17
kwin is the only window decorator that i know is in the repos, but i would think that it would be installed with kde-core as it is the default kde window decorator

---

