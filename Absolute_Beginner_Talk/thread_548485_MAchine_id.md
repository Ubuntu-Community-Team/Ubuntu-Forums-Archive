---
title: "MAchine id"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by IsKall on 2007-09-11
I need to obtain my machine id for installing Mathematica 6 but I don't know what the command is, any who knows?

---

### Post by Skrynesaver on 2007-09-11
Mathematica uses the MAC address of your first NIC as a machine identifier.

```

ifconfig eth0 |grep HWaddr|awk -F'HWaddr ' '{print $2}'

```

Will return your MAC address

---

### Post by Steve1961 on 2007-09-11
Try uname -i

Edit: ignore the above, the previous poster was correct

---

### Post by IsKall on 2007-09-11
Thank you both, it worked.

---

