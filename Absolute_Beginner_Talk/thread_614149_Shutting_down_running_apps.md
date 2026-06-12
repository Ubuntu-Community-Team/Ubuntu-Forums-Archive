---
title: "Shutting down running apps"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by pcostanza on 2007-11-15
In trying to install Nvidia drivers manually in Envy, I have a message that I have to stop certain running apps before I can make any changes but I'm such a newb that I have no idea where to find the running apps.  I don't see anything under Services that mention the apps that need to be closed.  Please point me in the right direction.

---

### Post by taurus on 2007-11-15
What apps are we talking here?  Perhaps you can find them on this list.

Applications -> Accessories -> Terminal
```
ps -A
```

---

### Post by Hospadar on 2007-11-15
if it's the nvidia drivers, you probably need to shut down your x server
From a text terminal (ctrl-alt-F1) log in and do```
sudo /etc/init.d/gdm stop
sudo envy -t
```

---

### Post by pcostanza on 2007-11-15
> **Hospadar said:**
> if it's the nvidia drivers, you probably need to shut down your x server
From a text terminal (ctrl-alt-F1) log in and do```
sudo /etc/init.d/gdm stop
sudo envy -t
```

Yep, that's it.  Thanks much. This place is great for uber quick replies. :)

---

