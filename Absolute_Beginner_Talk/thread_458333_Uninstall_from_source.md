---
title: "Uninstall from source?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Dougie187 on 2007-05-29
Hey guys,
So this might be a stupid question, but im not sure. So i wanted to make sure i knew what i was doing before i screwed up something.

So I installed Pidgin from source. And now i want to upgrade to the latest. I was curious if i had to uninstall the previous version (which i dont know how to do from source), or if i could just installed the latest version and hope it works correctly.

Any help would be great. Thanks guys.

---

### Post by Sparkster185 on 2007-05-29
If you still have the directory around where you did your ./configure, ./make, sudo ./make install, then you should be able to do a "sudo make uninstall".

---

### Post by Dougie187 on 2007-05-29
I dont have it anymore. Do you think i could do the same thing with the new version of the source?

---

### Post by Sparkster185 on 2007-05-29
I can't guarantee it will work.  You could try to re-download the original tarball, uncompress and run ./configure, ./make and then try "sudo make uninstall".

---

### Post by Dougie187 on 2007-05-29
Thanks. That worked. Glad source forge has the old source files.

---

### Post by dpreacher on 2007-05-29
i was discussin this exact thing with a friend...good i verified it is make uninstall and not make remove...so umm..if sf doesn't have the old release...havin a copy of the original tar package wud help too .... right?

---

### Post by Dougie187 on 2007-05-30
Probably. I just made a Source folder, to put source of installed apps. That way i can use them to uninstall if i ever need to.

---

