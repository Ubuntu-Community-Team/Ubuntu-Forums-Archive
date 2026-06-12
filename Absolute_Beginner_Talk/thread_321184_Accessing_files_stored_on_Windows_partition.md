---
title: "Accessing files stored on Windows partition"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by fartsack on 2006-12-18
I have installed Ubuntu 6.10 on top of my XP box, and configured it with a dual-boot configuration.  After installing Ubuntu, I was pleased to see that I could see the contents of my Windows partition within the filemanager.  Now that I have visibility to my Windows directories from within Ubuntu, I'd like to know if it's possible to play the mp3s, display my pictures, and view/edit my documents that are stored on my Windows partition, but within Ubuntu and using the applications that come with Ubuntu.

Let me know if this doesn't make sense, and I'll try to clarify.

thanks in advance !

/fartsack

---

### Post by bodhi.zazen on 2006-12-18
Yes you can. Use the appropriate application in Ubuntu.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by annda on 2006-12-18
if you can see the files, you will probably be able to view/play them. editing is more tricky, because XP uses an NTFS filesystem by default, which is read-only under linux.

there are some drivers (but not 100% safe) that will let you write to your NTFS partition. search the forums if you really need write access.

---

