---
title: "interupted update has stopped other updates working"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by jfossill on 2008-03-07
I have only just installed Ubuntu on to my comptuer( yesterday) and during an update this morning the power was switched off my computer in the middle of an update.  now i have had to log on with a different sesison just to get on and updates are not working.  when i try to do anything to do with updates i get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i have tried to run this file, but am very new to this and cannot seem to fix it myself.

any help would be great

Cheers

---

### Post by kesman on 2008-03-07
so you have tried to run
```

sudo dpkg --configure -a

```
in terminal?

After this, run
```

sudo apt-get update
sudo apt-get dist-upgrade

```
to resume the updating.

---

### Post by jfossill on 2008-03-07
thank you very much! worked great

---

