---
title: "Webcam with multiple users"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Juan_VCS on 2007-01-14
I'm running edgy and I have two users accounts. One has administrative privileges and the other doesn't.
The webcam works well with amsn in the admin account, but in the other, it isn't even recognized.
How do I get it to work on both?

---

### Post by Juan_VCS on 2007-01-14
Well, I got the answer from the #amsn IRC channel @ freenode:

<frying_fish> Juan: sudo vim /etc/group
<frying_fish> it will be in there
<frying_fish> or replace vim with the editor of your choice.
<Juan> well, i see video now
<frying_fish> stick the users in that group
<Yoda-BZH> adduser youruser video

---

### Post by docshawnc on 2007-01-25
Jeez - it's amazing what gems you can find if you did around here long enough.  I was going crazy with this same problem - thanks!!!!!!!!!!!

---

### Post by cje on 2007-09-22
Thanks for the thread - I had the same problem.

---

