---
title: "unable to sources.list"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2006-09-01
I read a thread here a while ago where someone was unable to edit their sources.list file. I am having a similar problem.. their solution was to reinstall or at least that's what they did.

There was a person in that thread and they suggested coping the old sources.list to a new one (which is what I did) and it' seems to work. 
I guess my question is why in the world would sudo not allow me to edit my sources.list file?

Is this a larger problem (is there a fix?) that I could run into?

Am I going to have to reinstall in order to ensure I am not going to continaully have to copy a file I am not allowed to access as root to a new one?

Just curious if this is an ongoing problem and what I could do to remedy it.

Thank you!

---

### Post by professor_chaos on 2006-09-01
I've never heard of this.
Can you post the output of these commands

ls -l /etc/apt/sources.list
lsattr /etc/apt/sources.list

---

### Post by cjnkns on 2006-09-01
Hi Professor!

Sadly I already replaced my sources.list so the permissoins are different.
Here is another file from that directory though. Hope this helps....

-rw------- 1 root root 0 2006-05-30 19:51 secring.gpg
----------------- secring.gpg

---

### Post by Bachstelze on 2006-09-01
sudo will allow you to edit _anything_, given that the file is there. Please be more precise, what happens when you want to edit the file ?

---

