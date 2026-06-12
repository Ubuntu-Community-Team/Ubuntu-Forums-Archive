---
title: "command line via ssh"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by Hotchilli on 2005-12-28
what is the command to start the firefox gui via ssh

hc:smile:

---

### Post by Kyral on 2005-12-28
You mean on the computer you have SSH'd into?

Well first off you need to connect in a "special" way, that is enable X11 Forwarding in the command. Its quite easy

```
ssh -X username@host
```

Then the command should be just "firefox"

---

### Post by Refrozen on 2005-12-28
[sshd_config](http://manlib.com/man/476) must be configured to allow X11 Forwarding, and you have to connect with -X :)

---

