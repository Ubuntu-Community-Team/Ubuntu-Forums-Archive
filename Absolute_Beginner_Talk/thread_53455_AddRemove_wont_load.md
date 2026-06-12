---
title: "Add/Remove wont load"
date: 2005-07-31
forum: Absolute Beginner Talk
---

### Post by lifewillfadeaway on 2005-07-31
For some reason my add/remove programs list will not load it pops up and just keeps doing the little ubuntu symbol like its loading. Any help?

---

### Post by heimo on 2005-07-31
This could help:
[http://www.ubuntuforums.org/showpost.php?p=279761&postcount=29](http://www.ubuntuforums.org/showpost.php?p=279761&postcount=29)

Search gnome-app-install for more threads with same problem.

---

### Post by lifewillfadeaway on 2005-07-31
awesome thank you!  :)  but what exatcly did that do
PS. it works lol

---

### Post by heimo on 2005-07-31
Installed patched version of that application.
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871)

You should not install applications without package management, in long run it'll mess your system. This patch should probably be in Ubuntu repositories, but I don't know if it is. Was your system otherwise up to date?

 ```
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by lifewillfadeaway on 2005-07-31
Yeah except it kept saying firefox was out of date, but i believe that is because i had to edit some of the files to get Java2 runtime to work in it.

---

