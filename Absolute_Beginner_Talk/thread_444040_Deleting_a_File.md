---
title: "Deleting a File"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-15
So I need to delete a file from the trash that I have duplicates of on the machine. Problem being, they are locked files and I can't seem to unlock or delete them due to this. Is there a way to unlock them as a super user or just up and delete them. The folder I want to delete is already in my file system and I basically have duplicates of them, I've verified to make sure and just want to get rid of them but it's really itritating that I can't! Thanks in advance!! :) :guitar:

---

### Post by Najand on 2007-05-15
Use```

sudo rm -rv <PATH>/<FOLDER>

```
in the command prompt. If you are not familiar with commands, push Alt+F2 and type:
```

gksu nautilus

```
and try to delete your file there.

---

### Post by Tumpster on 2007-05-15
Alright, figured it all out! Thank you for you're help!! :)

---

### Post by bashologist on 2007-05-15
> **Tumpster said:**
> whats the path to my trash can?

~/.Trash/

---

