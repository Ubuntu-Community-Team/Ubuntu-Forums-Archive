---
title: "User corrupted"
date: 2007-04-30
forum: Apple PPC Users
---

### Post by tomos on 2007-04-30
Following a post from about a week ago, trying to match my ubuntu and osx file permissions for file sharing, I have corrupted my username until a login only lasts 10 seconds.  I am told at login that $HOME/.dmrc should be owned by the user (me) and have 644 permissions.

I think the damaging step was this:

sudo find / -user 1000 -exec chown 1100:211 {} \;

My not understanding this cost me.

My question is this: is it possible for me to recover any of the files owned by the corrupted username?  Fortunately, I do have another username with admistrative priviledges.


TIA

---

### Post by tomos on 2007-05-01
Answered on users list.  Create new user in same group as corrupted user and as root copy corrupted user files to new user  (and change ownership),

---

### Post by shay1 on 2007-11-02
I have just had the same problem whilst following the instructions in a computer magazine to install an anti-virus programme. In this case the administrator account of which there was only one became corrupted. I found a remedy for resetting the password but only get the menus for the ordinary user and not the expanded menus/ facilities I use to get on the administrator account. Do I have to find and re-copy the files as above or is there another route?

---

