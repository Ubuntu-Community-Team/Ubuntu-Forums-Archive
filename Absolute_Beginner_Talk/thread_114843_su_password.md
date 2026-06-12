---
title: "su password"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by oyersj on 2006-01-09
I just installed Ubuntu 5.10 (desktop). Standard install - did not ask me for the root password, so now I cannot access the system settings. Is there a "default" su or root password or do I need to reinstall?

Thanks.

---

### Post by Mustard on 2006-01-09
to set up a root password, use 

```
sudo passwd root
```

Here is some more stuff on sudo and root to read as well...

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Ubuntu has the root password disabled by default for security reasons.  If you don't wish to do things the 'sudo way', then you should definitely read the above link to avoid creating complications for yourself.  I would suggest you try working with sudo for doing administrative tasks, as thats the way Ubuntu was designed to work.

---

### Post by oyersj on 2006-01-10
Thanks. That helped quite a bit. Got it up and going now.

Scott

---

