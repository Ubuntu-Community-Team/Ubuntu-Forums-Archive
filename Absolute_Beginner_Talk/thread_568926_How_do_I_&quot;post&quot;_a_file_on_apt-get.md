---
title: "How do I &quot;post&quot; a file on apt-get?"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-10-06
Just courious, how do I make a program done by me avalible by apt-get? Must before be pre-tested and pre-qualified? Must I contact an Ubuntu programmer? Can be done automatically?

---

### Post by Frak on 2007-10-06
[http://doc.ubuntu.com/ubuntu/packagingguide/C/ubuntu-upload.html](http://doc.ubuntu.com/ubuntu/packagingguide/C/ubuntu-upload.html)

---

### Post by zolookas on 2007-10-06
Apt-get gets files from repositories. Repositories are listed in /etc/apt/sources.list file. You can either use link which Frak gave or contact one of the "masters of the universe" or create your own repository and tell others to add it.

---

### Post by Frak on 2007-10-06
> **Frak said:**
> [http://doc.ubuntu.com/ubuntu/packagingguide/C/ubuntu-upload.html](http://doc.ubuntu.com/ubuntu/packagingguide/C/ubuntu-upload.html)
Or use this and upload it to Revu if you packaged it yourself and it will be picked apart, reviewed, and if it is good enough, will be added to the Universe.

---

