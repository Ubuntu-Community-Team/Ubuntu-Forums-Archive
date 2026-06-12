---
title: "postgresql updating troubles"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-10-09
Whenever I try updating postgresql-8.2 via Update Manager, I get this error:

```
E: /var/cache/apt/archives/postgresql-8.2_8.2.5-0ubuntu0.7.04.1_i386.deb: subprocess new pre-removal script returned error exit status 102
```

This also makes it impossible to remove anything from Synaptic, because it tries to upgrade this before it removes anything.  Is there anyway to at least make it not try to update that when I try removing things through Synaptic?

Thanks.

---

### Post by Yes on 2007-10-10
I just tried removing it, and it didn't work.  I really need to fix this, I can't remove anything through Synaptic and the terminal.

---

### Post by Yes on 2007-10-13
Bump.

---

### Post by Yes on 2007-10-14
Could I just delete it from my usr directory?  I'd like to update to Gusty when it comes out, and you need to have everything from Feisty updated, so that's just one more reason for me to get this solved.

Thanks.

---

### Post by Yes on 2007-10-16
Anyone?

---

### Post by Yes on 2007-10-16
Solved by deleting the postgresql-8.2 entry in my /etc/r2.d/ folderand then updating postgresql-8.2 .

---

### Post by jasir on 2007-10-31
had similar error message when i tried to install the update for postgresql-8.2
mine was:
**subprocess new pre-removal script returned error exit status 1**

i tried to find /etc/r2.d/ folder like you said, but there wasn't one in mine.

but i managed to finally upgrade. here's what i did:
renamed the folder "postgresql" folder under /etc/ to "~postgresql"

ran the upgrade install. it finally worked, but with some errors.
i not sure if the upgrade was actually successful.. but at least its out of the update manager. :)

and finally renamed the folder back to "postgresql"

---

