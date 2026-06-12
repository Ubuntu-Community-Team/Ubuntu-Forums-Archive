---
title: "after logon screen get this error"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by broekskw on 2006-12-10
this one is from my good computer running ubuntu. after i type my user and and then password and enter i get this message come up, can someone tell me whats up and how to correct this. thanks

user's $home/.dmrc file is being ignored. this prevents the default session & language from being saved. file should be owned by user & have 644 permission, user's home directory must be owned by user & not writable by other users.

---

### Post by furiousV on 2006-12-10
> **broekskw said:**
> this one is from my good computer running ubuntu. after i type my user and and then password and enter i get this message come up, can someone tell me whats up and how to correct this. thanks

user's $home/.dmrc file is being ignored. this prevents the default session & language from being saved. file should be owned by user & have 644 permission, user's home directory must be owned by user & not writable by other users.

try in console

```
mv .dmrc .dmrc-old
```

To get into the console youll have to press **control+alt+F1**

Then once you done the rename, **Control+alt+F7** to get the login screen back. 

What should now happen is when you login, a new .dmrc file will be created.

---

### Post by broekskw on 2006-12-10
thanks will give that a try then reboot
:D

---

### Post by broekskw on 2006-12-14
furiousV i tried your command in console and did a reboot but still get the same message.anything else to try?

thanks:mrgreen:

---

