---
title: "1962 no operating system found"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by bosconermal on 2007-01-01
My computer was working fine, I turned it off, then later turned it back on again and now it says "1962 No operating system found."

The hard disk is fine-- I checked with Knoppix and everything seems to be there.

What do I do now?

---

### Post by K.Mandla on 2007-01-02
Your boot sector may have been corrupted, so that your BIOS can't pass the boot sequence on to an operating system. Try 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

or

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

No guarantees, but it might help.

---

### Post by h0ax on 2007-01-02
Have you tried memtest86? - comes default on ubuntu disk

---

### Post by bosconermal on 2007-01-07
Yes that was it. Thank you very much! It's back as good as ever

---

