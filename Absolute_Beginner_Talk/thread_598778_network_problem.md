---
title: "network problem"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by leras on 2007-10-31
i have install ubuntu 7.10 and vmware server console then i pun windows xp into vmware and i enable host only a private network shared with the host
so when iboot xp i find the other pc (ubuntu)but when iam tryiing to connect it asks me a user name and a password everything that i tried i cant connect i think its a samba problem but i dont have any idea to fix it

---

### Post by greenlegacy on 2007-11-01
On the ubuntu side you'll need to add a password for your user name.  Use these commands:

```

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

```

---

