---
title: "need admin access"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by BillGod on 2007-11-02
ok here's the situation.  I setup the kid next doors computer a long time ago on ubuntu.  For some unknown reason today he created a new user and deleted his old.  now he is stuck with an account with no sudo access.  Besides a reload anyone got any ideas?  And no I never changed the root password to something that I would know.  default install.

Bill

---

### Post by jordanmthomas on 2007-11-02
Boot into recover mode (there should be an option in Grub) and run this:
```
usermod -aG wheel $HISNEWNAME
usermod -aG admin $HISNEWNAME
```
(replacing $HISNEWNAME with his new account name, of course)

I'm not sure if Ubuntu uses the wheel account, but it should.

---

### Post by reckless2k2 on 2007-11-02
some one help me on this but i believe you can access via recovery mode and work it out there. set a root password, make a user with admin privs, or set the new user with admin privs. more than likely he did not delete the old users files either...only the user itself. boot into recovery mode and peek around.

---

### Post by BillGod on 2007-11-02
wont I still need root password with recovery mode?

---

### Post by jordanmthomas on 2007-11-02
No, which is one thing I hate about Ubuntu.  Anyone can boot into recovery mode and unless a root password has been set, it logs you in as root.

(of course, if they have physical access to be able to pick it from Grub you're screwed anyway...so it's not too big a deal I reckon)

---

### Post by BillGod on 2007-11-02
That will save him if it works.. ( I usually reset root password so I never noticed)  Thanks a ton

Bill

---

### Post by jordanmthomas on 2007-11-02
If there is a root password, though, you'll either have to know it or know how to get around it (maybe mount from a LiveCD and edit /etc/groups?  I'm not sure what to do if it doesn't work).

---

