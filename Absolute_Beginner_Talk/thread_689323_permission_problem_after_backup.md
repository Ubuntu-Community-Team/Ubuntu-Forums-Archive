---
title: "permission problem after backup"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by bittergourd on 2008-02-06
hi
i stupidly copy all my files onto another disk (boot from liveCD), format the old one and moved back all the files, instead of using tar.  i changed the fstab so that it mounts partition correctly and is able to boot up to the log in window.  but when i tried to log in, it complains about not having 644 permissions to my $home.

i suppose that the problem was about permission and the owner was changed because of moving back and forth.  any idea how to change the owner of the home dir (and necessarily other system files) back to normal?

thx

btw the home dir located on an separate partition.

---

### Post by jken146 on 2008-02-06
Assuming your username is bob, ```
sudo chown -R bob:bob /home/bob
```

You can press Ctrl+Alt+F1 when you get to the login screen to switch to a terminal, then Ctrl+Alt+F7 to switch back.

---

