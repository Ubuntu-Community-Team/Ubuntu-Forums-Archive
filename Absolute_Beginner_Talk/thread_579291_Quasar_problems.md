---
title: "Quasar problems"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by MichaelSM on 2007-10-18
Hi again.

Advice requested ...

I've installed but cannot access a program called Quasar which is an accounting package from LinuxCanada. Basically I managed to install the program, along with the GUIs and menu items.

Everything before and after the following command sequence is fine. Trouble is that I input incorrect passwords (my own) when all that was needed -turns out later- was 'quasar' and 'quasar.' In other words I need to wipe anything I did in this Terminal session, where superuser and passwords were originally entered wrongly and encrypted.

su postgres
createuser -d -E -P quasar-dba
createuser -E -P quasar
exit


Is that enough info? I have to kill that session and its entries and re-enter the generic passwords.

I can get into the Quasar Admin GUI, by entering my root password, but can't fix things that way. I'm REALLY starting to like Terminal..

This is a weirdo thread. 

Thanks to all, yet again.

Mike.

---

### Post by tkharris on 2007-10-18
Assuming these are just normal postgres users, you can do this:

```

ALTER USER quasar-dba WITH PASSWORD 'newpassword';
ALTER USER quasar WITH PASSWORD 'newpassword';

```

---

### Post by tkharris on 2007-10-18
Oh, and if you just want to delete them completely ( which looking back it looks like you do ):

```

DROP USER quasar-dba
DROP USER quasar

```

---

