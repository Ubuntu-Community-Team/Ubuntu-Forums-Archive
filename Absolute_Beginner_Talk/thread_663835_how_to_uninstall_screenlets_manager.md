---
title: "how to uninstall screenlets manager?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Rubruquis on 2008-01-10
I want to uninstall the screenlets manager because it sometimes gives an error at the beginning about Demon and I don't use screenlets at all anyway.

I've installed it with adding to sources.list and then with the command sudo apt-get (that was how the guide told me to install it).

How am I going to uninstall it?

---

### Post by Rubruquis on 2008-01-10
I've searched the forums a lot but all the methods offered were for direct download from web and untarring. But my install method was different (as mentioned above)
So I don't want to mess things up.

Anyone knows how to uninstall it?

---

### Post by PeterJS on 2008-01-10
Open up synaptic, search for screenlets, and remove it.
or
```

sudo apt-get remove screenlets

```

---

### Post by Deadmode on 2008-01-10
you can remove it from synaptic manager or if you prefer doing it from terminal. you can do 
```
apt-cache search (Program name)
```

after you've found the aptitude name you can remove it.
```
sudo apt-get remove (Program name)
```

If you want to remove the configuration files as well you can type
```
sudo apt-get remove --purge (Program name)
```

---

### Post by Rubruquis on 2008-01-10
Thanks a lot!

---

