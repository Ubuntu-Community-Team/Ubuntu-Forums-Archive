---
title: "Changing profile without shell"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by maXx_ on 2008-01-21
Hello, i'm as new as they come to ubuntu (wubi install)
 i was messing around with my shell profile (whichever the default shell is), and I marked the area that said instead of running my shell run this command: "sh PS1="% ", thinking sh was to open a shell, and PS1="% " to get my shell to just have "%" instead of "username@ubuntu:". So setting that profile as the default, my shell just opens and then automatically closes, which is bad.. any suggestions?

---

### Post by shearn89 on 2008-01-21
I'd hit ctrl-alt-f1 to get to a real console, then log in as usual, and replace your .bashrc file with the default skeleton one:
```

ctrl-alt-f1
#login as usual
cp /etc/skel/.bashrc .bashrc
sudo chown <your username> .bashrc

```

That should work. Post back if it doesn't.

---

