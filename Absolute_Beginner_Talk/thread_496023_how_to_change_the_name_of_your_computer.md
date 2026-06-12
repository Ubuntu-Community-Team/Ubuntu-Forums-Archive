---
title: "how to change the name of your computer"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Akuma Shiro on 2007-07-08
Remember when you first installed Ubuntu, and you had to give the name to your computer as it would appear on a network? Well, I discovered:confused that I misspelled the name I gave me computer, and now would like to change it without reinstalling Ubuntu.

How would one go about this task?

---

### Post by erimar77 on 2007-07-08
```
sudo gedit /etc/hostname
```

---

### Post by rharris on 2007-07-08
Go to System-Administration-Network, highlight your connection then click on the General tab, under Host settings will be an entry for the host name. You can change it there. Close and restart for the change to take effect.

Rob

---

### Post by Akuma Shiro on 2007-07-08
> **rharris said:**
> Go to System-Administration-Network, highlight your connection then click on the General tab, under Host settings will be an entry for the host name. You can change it there. Close and restart for the change to take effect.

Rob

Thanks! 
Worked like a charm!

---

### Post by steve.horsley on 2007-07-08
> **erimar77 said:**
> ```
sudo gedit /etc/hostname
```

Unless you change /etc/hosts at the same time, you will break Gnome and not have a GUI. It is better to use the networking administration GUI, which will change both without making any typing errors.

---

