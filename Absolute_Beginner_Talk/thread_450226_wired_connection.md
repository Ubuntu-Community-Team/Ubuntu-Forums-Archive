---
title: "wired connection"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by khcbaser on 2007-05-21
I am new in Linux and need help.
I want to get wired to internet via  intranet. I enter DNS particulars but cannot get connected. Please help.
:(

---

### Post by viciouslime on 2007-05-21
We'll need a little more info, where are you entering this information, can you describe how your network is setup?

---

### Post by jgf621 on 2007-05-21
I also need networking help.  I'm running Ubuntu 7.04 and have connected successfully to two PC's running XP and the Internet.  I have two Ubuntu machines and am at a loss how to connect between them.  Connection is through a wired router and I can ping one from the other but that's it.

Thanks,

joe

---

### Post by Cypher on 2007-05-21
> **jgf621 said:**
> I also need networking help.  I'm running Ubuntu 7.04 and have connected successfully to two PC's running XP and the Internet.  I have two Ubuntu machines and am at a loss how to connect between them.  Connection is through a wired router and I can ping one from the other but that's it.

Thanks,

joe
Please don't hijack threads..:)

As far as connecting between two Ubuntu machines go, you'd want to install the SSH server and client on both machines.
Do
```

sudo apt-get install openssh-server openssh-client

```

---

### Post by jgf621 on 2007-05-21
Thanks for the help. SSH client and server install cured symptoms.  Sorry to have violated protocol.  Please chalk it up to inexperience.

---

