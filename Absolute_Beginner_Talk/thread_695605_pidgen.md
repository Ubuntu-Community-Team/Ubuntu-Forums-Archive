---
title: "pidgen"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by rburkartjo on 2008-02-13
i have pidgen installed on my desktop. my daughter recently set up a user account. i want her to be able to access the pidgen account on my desktop.reason she has all her buddies on it and setup the way she likes it. when i go to her desktop the only way i can use pidgen is to reinstall it from the application menu and of course that means she will have to reinstall all her contacts./tks ray

---

### Post by Crooksey on 2008-02-13
Cant you just install pidgin on her machine, then copy over the ~/.pidgin directory to her computer, as long as the usernames are the same it will be fine.

---

### Post by rburkartjo on 2008-02-13
user names are not the same she has own user name.

---

### Post by Crooksey on 2008-02-13
If you copy the ~/.pidign from your computer, to hers it will work fine.

---

### Post by nemilar on 2008-02-13
You shouldn't have to re-add all the buddy information to the new pidgin install; that information is stored on AOL's servers (assuming you are using AIM).

But, if for some reason it doesn't work out, the buddy list is stored in:

~/.purple/blist.xml

Account information is stored in:

~/.purple/accounts.xml

After installing pidgin on her machine, just copy them over into her ~/.purple directory and it should load up correctly.  But I recommend just logging into the account and seeing if all the contacts are correct from the start, first.

---

### Post by nemilar on 2008-02-13
Ahh, I didn't read your post carefully enough :) It is not two computers, just two user accounts on one computer.

You can copy over the contacts from your account to hers, and it should appear fine.

---

