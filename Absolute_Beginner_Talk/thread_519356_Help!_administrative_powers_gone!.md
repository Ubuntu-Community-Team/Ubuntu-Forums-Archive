---
title: "Help! administrative powers gone!"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by axemurder785 on 2007-08-06
when i was adding another user i think i unchecked some of my abilities in the edit user thing and now i can't install anything, update anything, or edit users! please tell me how to fix this!

---

### Post by Cypher on 2007-08-07
At the GRUB menu, choose to boot into Recovery Mode. This will drop you to a SHELL prompt as Root. Now add your username to the "admin" group like so:
```

addgroup <username> admin

```
Put in your real username instead of <username> and you will see a message like:
> Adding user '<username>' to group 'admin' ...
Done.

Now "exit" from that shell to reboot the machine, allow it to boot into Ubuntu like it normally does, login and see if you've gotten your Admin pirivileges back..

---

### Post by Venoseth on 2007-12-28
Thanks a lot. I ended up doing the same thing by mistake. >.> I hate the filled/unfilled boxes... I'm still confused as to which is which. XD

---

