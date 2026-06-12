---
title: "All this software and games for android but not Ubuntu? (Compatible)"
date: 2013-06-26
forum: Any Other OS
---

### Post by Langney on 2013-06-26
Here's a question thats been bugging me for a while now. Why If they release an Android version of say Final Fantasy or GTA. Why Is there no Ubuntu or other Linux variant. As i understand Isn't Android Linux anyways? If it Is why don't developers spend that little extra time making It compatible. Or am I completely wrong? I know there are Android SDK out there but I don't see why we should be faffing around with emulation when we can have It native. Can someone please clear this up for me as It's been wracking my brains since learning Android Is linux.

---

### Post by MidnightGrey on 2013-06-26
probably something to do with the number of people using android smartphones vs people using linux.

---

### Post by cortman on 2013-06-26
A better understanding of what "Linux" is would help you. Linux is a kernel; a low-level software traffic director and software-to-hardware middleman. Just because two operating systems use the same kernel means almost nothing as far as binary compatibility, which means program/app compatibility. This is why there are so many operating systems that use the Linux kernel but are not binary compatible (Debian/Ubuntu/Fedora/Slackware/Arch, etc.), and why despite the fact that most people like to mock Richard Stallman for his insistence on using the term "GNU/Linux", it really does put the OS in better context- the GNU tools (and many other pieces of software) using the Linux kernel.
Android apps are written in Java against Android-specific APIs. They can be run in emulation mode in Ubuntu (or at least used to be able to) but to make it work natively on Ubuntu would mean pretty much a total rewrite.

---

