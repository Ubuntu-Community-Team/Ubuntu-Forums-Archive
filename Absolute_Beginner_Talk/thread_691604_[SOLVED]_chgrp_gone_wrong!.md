---
title: "[SOLVED] chgrp gone wrong!"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by reeksy on 2008-02-08
Hi

I've made a little mistake! Whilst logged in as root i ran the following whilst in /etc/

```

chgrp -R cvsusers . 

```

which was a big mistake! I should have ran the command whilst in /usr/local/cvs/.

Since restarting i cannot login as root. When i sudo su i get the following:

```

# sudo su
sudo: /etc/sudoers is owned by gid 1001, should be 0

```

Is there anyway out of this? I  need to reset the group on every file within /etc/ back to root! I'm stuck!

Regards
Jon

---

### Post by taurus on 2008-02-08
You need to boot into recovery mode from GRUB menu and change the group of /etc/sudoers back to root again.

```
chgrp root /etc/sudoers
shutdown -r now
```

---

### Post by reeksy on 2008-02-08
Great thanks ill try this now

---

### Post by reeksy on 2008-02-14
Worked like a charm. Thanks!

---

