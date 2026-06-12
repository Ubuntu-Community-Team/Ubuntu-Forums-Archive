---
title: "performance improvement"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by blue42 on 2005-11-26
Hey
    This topic has already been hashed through prviously but I can't go through 74 pages to find it so I apologize for bringing it up again. I've read the suggestion of using xfce as a window manager to improve performance and tried it out. Hopwever one of the programs I use, Audacity, crashes when I try to move large segments of track, yet windows98se handles these and larger with no problems. my machine is a amdk6/450 with 256m of memory. Are there other options I can use or is their a way of shutting down some of the background processes that are taking up memory. I'm not that knowledgeable about linux processes so I don't know what should or should not be running or even how to prevent them from starting up.

---

### Post by ssam on 2005-11-26
do you have swap enabled?

can you post the output of
```
swapon -s
```

the crashing maynot be related to lack of memory.

```
top
```
is quite good for seeing which processes are using lot of memory. but linux memory figures are rather confusing. (some memory can be shared between applications, and gets counted twice).

what size audio formats are you using?

---

### Post by blue42 on 2005-11-26
Not sure what you mean about Audacity, but the tracks are set at 44100 mhz and 32 bit float. I'd like to keep this setting if it provides the best output. I tried the swapon command and it spit out a statement similar to what you'd find in fstab and the swap partition is listed in fstab.

---

### Post by ssam on 2005-11-26
programs should not just crash if they use too much ram (unless they use up all of you swap space). if you only have 256mb ram and a small amount of swap then that may cause crashes if you work with 100mb files.

if you are working with 10mb files then the crash is a bug in the program.

you should probably twice or three times the amount of ram as your largest file. swap is a slow substitute for ram.

---

