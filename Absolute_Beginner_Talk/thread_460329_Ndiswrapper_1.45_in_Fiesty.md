---
title: "Ndiswrapper 1.45 in Fiesty"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by blue22 on 2007-05-31
Hello,

I have downloaded Ndiswrapper-1.45 and am having trouble installing it.  Everything goes as according to the instructions until **make install** is run.  It comes up with a long list of error messages but the first of which is as follows:

**loadndisdriver.c:15:20: error: stdlib.h: No such file or directory**

Has anyone got an idea of either what I may be doing wrong or a way round this problem?

Blue22

---

### Post by bmartin on 2007-05-31
I don't really have any idea what would be wrong. **make install** shouldn't be looking for .h files at all. When compiling ndiswrapper, you should perform the following steps:

[LIST=1]
[*]**sudo make uninstall** until no more messages appear at the bottom of the output
[*]**make**
[*]**sudo make install**
[/LIST]

I've compiled this by hand myself and have written a script that automatically compiles it and installs the Broadcom 43xx drivers (a separate script).

Let me know where I can download the drivers for your card and how to extract them (via PM). I'd like to add support for more wireless chipsets. If it just so happens that your chipset is in the Broadcom 43xx family, PM me and I'll send you a link to my other post.

---

### Post by e.stryker on 2007-06-05
If it can't find stdlib.h, then you probably can't compile anything. 

perhaps try running:

```
apt-get install build-essential
```

This may be overkill, but it should do the trick.

---

