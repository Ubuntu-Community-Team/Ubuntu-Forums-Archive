---
title: "[SOLVED] Dependency error when installing Miro"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by machavillain on 2007-11-18
Trying to install Miro as described [here]("http://www.getmiro.com/download/ubuntu.php"). For package "miro", I get this error:
```
miro:
Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed
```

Package "miro-data" works fine. Any ideas?

[[cross-posted]("http://www.getmiro.com/forum/comments.php?DiscussionID=487") to Miro forum]

---

### Post by machavillain on 2007-11-19
Any ideas? Little help?

---

### Post by machavillain on 2007-11-20
Bump.

---

### Post by justU on 2007-11-22
I have the same problem! Had someone success with the miro-1.0 repo?

---

### Post by zvacet on 2007-11-22
Go[here](http://packages.ubuntu.com/gutsy/libs/libpango1.0-0)and chek that you have all dependencies installed.When you do install package.

---

### Post by justU on 2007-11-22
> **zvacet said:**
> Go[here](http://packages.ubuntu.com/gutsy/libs/libpango1.0-0)and chek that you have all dependencies installed.When you do install package.
Our problem is not that libpango couldn't be installed! Our problem is that libpango is too old!
zvacet, your link points to "libpango1.0-0 (1.18.2-0ubuntu1)", but miro needs libpango1.0-0 (>=1.18.3)!

The needed package isn't available in the official gutsy repository!

---

### Post by justU on 2007-11-22
Ok, I solved the problem!

You will have to add the proposed repo to your /etc/apt/sources.list
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted

**EDIT:** You don't need the gutsy-proposed repo. The needed libpango version is also in gutsy-updates!
The update repo was deactivated on my machine...

---

### Post by machavillain on 2007-11-24
That worked! Thank you.

---

### Post by doseryder on 2007-12-05
> **justU said:**
> Ok, I solved the problem!

You will have to add the proposed repo to your /etc/apt/sources.list


**EDIT:** You don't need the gutsy-proposed repo. The needed libpango version is also in gutsy-updates!
The update repo was deactivated on my machine...

My problem did not pertain to Miro but gtkpod also needed libpango-1.18.3 and by adding the gutsy-proposed repo it worked. :>

Thx

---

### Post by shafin on 2007-12-07
Thanks,I just needed to upgrade compiz and ran into the same problem.
Ubuntuforums never stop to amaze me,anything is just a search away.

---

