---
title: "firefox problems"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Ionamay on 2007-11-18
I am using ubuntu 7.10 and I have some problems with firefox. when I type a ' as in the word 'don't' i have to put a space after the apostrophe or else the computer will beep. also it looks strange, narrow, for example when i see a circle on firefox it looks like an oval.

Also can I rename my hard drives? instead of disk-1 disk-2, etc.

---

### Post by Beaucephus on 2007-11-18
Never seen the firefox issue...

The name of the disks comes from the volume label if one exists.  Yours evidently do not have labels.  I usually set the label when formatting the drives, so my method is probably no good.  There is a tool for applying volume labels out there somewhere.

---

### Post by teryowen on 2007-11-18
The fact your seeing ovals is because your resolution is wrong.
as for the ' im not sure what your talking about.

But to get rid of the beeps do the following:

add this line:
```
blacklist pcspkr
```

to the end of this file: /etc/modprobe.d/blacklist

---

