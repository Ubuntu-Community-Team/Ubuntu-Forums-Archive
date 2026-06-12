---
title: "login issue"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by vizual_eyez1 on 2007-04-01
During the installation of Ubuntu I was never asked to give a root password or to set up a user account. After the installation finished I was prompted for a username and password. I obviously didn't have one. I went online to see if there was a remedy for this and was told that I could interrupt the grub. Maybe I was doing something wrong while trying to interrupt the grub because it wasn't working. Back to the original issue!! Is there something that I can do to enable me to login at all. I'm frustrated and don't know what my options are, if any.:icon_frown:

---

### Post by NeoLithium on 2007-04-01
It sounds like it did an OEM install; so try using 
```

oem
```
As the username and password.

Once you login, type this command in terminal to create your login:
```

sudo oem-config-prepare

```

Hopefully this helps.
Neo

---

### Post by vizual_eyez1 on 2007-04-05
Thanks for the help. Everything is good now.

---

