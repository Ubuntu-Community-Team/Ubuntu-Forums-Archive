---
title: "can I safely delete this folder?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by clevin on 2007-05-29
I established a user acc called "test", for the purpose of some test operations. now I don't use it anymore, so i delete this user account from _users and goups_ of _system menu_, But afterward, I found the folder test" in /home is still there? so can I safely remove it without causing any trouble to the system?

---

### Post by ramjet_1953 on 2007-05-29
That shouldn't be a problem, as long as the test account has been removed.

However, you will need to sign into Nautilus with sudo privileges to do so.

In a terminal type in this:

[COLOR="Red"]gksu nautilus[/COLOR]

Regards,
Roger :cool:

---

### Post by joe.turion64x2 on 2007-05-29
It is not a problem if you don't mind what is stored there.

---

### Post by homergreg on 2007-05-29
That feature of leaving the home folder is there, among other reasons, so if someone in the same group as the user "test" can still use the files.  Think of it like if your linux box as at a corporation and you "test" got canned and you wanted to delete his account, but "test" had files on your system.  This allows the administrator and group members to still access those files until they are moved or no longer needed.  

So if you won't miss the files in test's home folder, feel free to delete.

---

### Post by Ek0nomik on 2007-05-29
If you don't need the files, you can also use the terminal:

```
cd /home
rm -r test
```

---

### Post by clevin on 2007-05-29
thanks guys

---

