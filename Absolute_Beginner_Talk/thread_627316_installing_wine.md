---
title: "installing wine"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by andvan on 2007-11-30
I am trying to install wine and I get this message:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by PmDematagoda on 2007-11-30
You will have to close Synaptic or any other package managers before installing Wine.

---

### Post by andvan on 2007-11-30
I am new at this how do I check other package manager?

---

### Post by PmDematagoda on 2007-11-30
If there are applications such as Synaptic running on the Desktop then simply close them:).

---

### Post by andvan on 2007-11-30
I have nothing else running on the desktop other than the terminal

---

### Post by PmDematagoda on 2007-11-30
If you are sure then open up your file manager using:-

Ubuntu:-
```

gksudo nautilus
```

Kubuntu:-
```

kdesu konqueror
```

Xubuntu:-
```
sudo thunar
```

Then navigate to the /var/lib/dpkg directory and simply remove file named lock. 

Then try installing Wine again.

---

### Post by andvan on 2007-11-30
Thanks a lot I got it to work.

---

### Post by PmDematagoda on 2007-11-30
Good to hear that:), could you mark the thread as Solved so that it could benefit others.

---

