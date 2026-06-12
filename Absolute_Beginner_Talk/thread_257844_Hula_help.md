---
title: "Hula help"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by wakaimono on 2006-09-15
Ok, as a n00b I have been trying to set up an email server. According to the instructions, I think I have done everything correct. I followed the inst found on the [WIKI]("https://help.ubuntu.com/community/Hula") but am having some difficulties. Error I get is 
Driver MDBLDAP failed to load: Driver MDBLDAP, Init failed with: Could not initialize LDAP connection
Insufficient privileges; shutting down.
ERROR: hula.libs error: MsgInit() failed

Any ideas, would really like to dump windows completely...:D

---

### Post by risbac on 2006-09-15
Ok, from what I read, it won't run because of a lack of privileges.

So maybe try to run it as a root: sudo ........
If it works, means that you have to set the correct rights for some files.

If it still doesn't not work, means that it's an internal problem of the software, like you are using an account without enough rights. Then you need to set this in the configuration of hula.

It's only two possibilities, and I don't know what is Hula. But that's what I would check. 

Be careful that running it as root is NOT a good idea, it's just to understand better where is the problem! 

Hope it will help a bit...

---

### Post by wakaimono on 2006-09-15
Tried running under sudo and as root, that is still the error. Hula is an e-mail and calendar server.

---

