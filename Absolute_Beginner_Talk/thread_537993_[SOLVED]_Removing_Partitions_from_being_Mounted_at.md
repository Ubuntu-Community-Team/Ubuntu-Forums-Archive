---
title: "[SOLVED] Removing Partitions from being Mounted at Boot"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Matuku on 2007-08-29
This is the issue; I (for some unknown reason) had a 500mb partition (ext2) just sitting around gathering dust (I don't know why it was there, think it was from a previous attempt at ubuntu). So I decided to get rid of it. My Live CD wasn't working so I went into my windows partition and proceeded to delete it from there. However, now, when I boot Ubuntu it goes into a fit having errors that it can't mount this disk and takes me into a Maintenance shell. I can get rid of this easily enough (typing "exit") and it continues to boot as normal, but how can I stop it from doing this? Can I simply edit something? Or may it have to be a reinstall?

---

### Post by Inxsible on 2007-08-29
post your fstab. Maybe you can disable the automount feature there and be done with it.
```
cat /etc/fstab
```

---

### Post by Songwind on 2007-08-29
Put a # in front of the line that refers to it in /etc/fstab

---

### Post by Matuku on 2007-08-29
Ok those were possibly record-breakingly fast replies. Will try that now.

EDIT: Worked like a charm; thought there must be something like that but didn't know where to find it. Another bandage on the ubuntu I keep breaking in places (thats what I love about Ubuntu; it feels gritty and as though you are actually working **with** the computer rather than **on** it as with windows).

Thanks for the speedy replies!!

---

