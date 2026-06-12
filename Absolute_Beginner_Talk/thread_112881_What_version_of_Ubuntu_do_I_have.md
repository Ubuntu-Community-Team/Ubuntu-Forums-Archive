---
title: "What version of Ubuntu do I have?"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by marty922 on 2006-01-05
G'day all,

I've been playing with Ubuntu for the last few days and have sorted most things out - DVD burning/viewing, MP3, video codecs etc.

But, how do I determine what ver of Ubuntu I have?  Is it enough to look at /etc/apt/sources.list and see that the cdrom line has Breezy Badger?

I reckon I'm ready to get rid of the Winblows partition fairly soon, thanks mainly to this forum - the HOWTO's are fantastic.

Cheers,

Marty.

---

### Post by SavageBeginner on 2006-01-05
Yea, basically if /etc/apt/sources.list has breezy everywhere, then you are using the breezy packages and have the breezy system installed.

---

### Post by Norberg on 2006-01-05
Yes it shulld be enough to look at /etc/apt/sources.list and see that the cdrom line has Breezy Badger.

---

### Post by carlosqueso on 2006-01-05
```
lsb_release -a
``` in a terminal will tell you too.

---

