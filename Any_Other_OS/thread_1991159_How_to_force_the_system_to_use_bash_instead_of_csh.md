---
title: "How to force the system to use bash instead of csh"
date: 2012-05-30
forum: Any Other OS
---

### Post by legolas_w on 2012-05-30
Hi,

What should I change in the system to make it possible for the ssh client to have bash when they connect instead of having csh?

When I connect to the server using ssh and invoke echo $SHELL it shows /bin/csh, I want to change it to /bin/bash.

Thanks.

---

### Post by 2F4U on 2012-05-30
I am not familar with RHEL but you might try this:

[http://serverfault.com/questions/162018/force-ssh-to-use-a-specific-shell](http://serverfault.com/questions/162018/force-ssh-to-use-a-specific-shell)

---

### Post by 1clue on 2012-05-30
Log in as the user in question and then type **chsh**

---

### Post by codemaniac on 2012-05-30
try modifying the user and point to bash as her default shell .
```
usermod -s /bin/bash username
```

---

