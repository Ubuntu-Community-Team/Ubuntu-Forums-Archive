---
title: "user profile synchronizing with different languages"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by mchnhed on 2007-08-06
I would like to setup one user account and then be able to synchronize various settings (e.g. Gnome, Applications, etc.) with all other user accounts. The only thing is that each of my user profiles have different default languages. Is that possible to keep these user profiles synchronized, while ignoring the language settings? If so, how could I go about doing it? Thanks in advance!

---

### Post by Pragmatist on 2007-08-06
> **mchnhed said:**
> I would like to setup one user account and then be able to synchronize **various settings** (e.g. Gnome, Applications, etc.) with all other user accounts....
Are you referring to the user settings that reside as hidden files in each user's home directory?

If that is what you want, then I don't know if any of those settings are language specific.  There should be a "LANGUAGE" variable for each user.  To see what it is set to, type:
```
 env |grep LANGUAGE
```

The reason for that variable, is so that each user can set it and all programs will reference it to know what language to use.  I don't know if all programs use the variable, however.

---

### Post by mchnhed on 2007-08-20
I am referring to the user-specific settings, such as the Gnome and Nautilus settings, including the icons listed on the panel. I would like to synchronize these settings between user profiles, disregarding the language (which you clarified is an environment variable, so that shouldn't be a problem).  Anyone have any idea how to do this?   :confused:

---

