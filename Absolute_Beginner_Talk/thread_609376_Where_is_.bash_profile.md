---
title: "Where is .bash_profile?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Patriot1776 on 2007-11-10
Can anybody tell me where the '.bash_profile' file is?  I'm wanting to give shell scripts a try, but I need to know where this is first to help with the learning process.

---

### Post by jaybombalous on 2007-11-10
your ~/ directory


edit: its hidden by default
edit edit: if its a personal settings file, which .bash_profile is, then it will always be in the 'users' home directory. Because each user can have his/her own profile, settings are loaded by default out of the current users home directory.

---

### Post by Bachstelze on 2007-11-10
And if you don't have it, just create it putting whatever you need in it ;)

---

### Post by taurus on 2007-11-10
And if you don't have one, create it.

Applications -> Accessories -> Terminal
```
ls -la ~/.bash_profile
touch ~/.bash_profile
```

---

### Post by Patriot1776 on 2007-11-10
That'll be even easier.  I've got Yakuake installed so the command-line is only a tilde keypress away.  Thanks everybody!

---

### Post by conehead77 on 2007-11-10
If you need to find a file in future you can always use "locate"
```
locate .bash_profile
```
for example

---

