---
title: "ifconfig problem..."
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by nightrider.36 on 2006-12-23
When I type in:

     ifconfig eth1 down

I get:

     SIOCFFLAGS: Permission denied

What does this mean?

---

### Post by Sef on 2006-12-23
Have you tried it this way:

```
sudo ifconfig eth1 down
```

---

### Post by 5-HT on 2006-12-23
It means your user does not have sufficient privileges to execute that command. This is completely normal, please read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more information
 
To disable your NIC:
```
sudo ifconfig eth0 down
```or

```
sudo ifdown eth0 
```

---

