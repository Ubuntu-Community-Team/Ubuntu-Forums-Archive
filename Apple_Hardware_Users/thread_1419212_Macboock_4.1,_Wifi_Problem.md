---
title: "Macboock 4.1, Wifi Problem"
date: 2010-03-01
forum: Apple Hardware Users
---

### Post by maliqu3 on 2010-03-01
I have followed how to install the wifi driver correctly and it worked. However, sometimes i face problems after that.
first problem, after i shutdown my macbook and tried to turn it on again, the wifi couldn't find my home network where it usually connects automatically.
second, even it shows that there are networks available, it couldn't connect to any network.


so anybody can help me? I'm tired when i face this problem even though sometimes it works properly. it happens many times since I installed Ubuntu 
9.10. it's only me who faces this problem in my house where all my friends don't.

Thanks

---

### Post by linuxopjemac on 2010-03-01
I can only say that I don't like the performance of networkmanager. I would switch to wicd:
```
sudo apt-get install wicd
```

---

### Post by maliqu3 on 2010-03-01
so, do i have to remove the network manager first then install the wicd or just install wicd without removing network manager?
Thanks

---

### Post by linuxopjemac on 2010-03-02
just install wicd, it will remove networkmanager by itself.

---

### Post by maliqu3 on 2010-03-02
thanks man, it works. hope i won't face the same problem again.

---

