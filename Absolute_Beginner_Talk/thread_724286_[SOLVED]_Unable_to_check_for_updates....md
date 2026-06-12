---
title: "[SOLVED] Unable to check for updates..."
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by chlorinekid on 2008-03-14
lately, when i try to check for updates using the update manager i get this error once i have entered my password:

> E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)

never had this problem before, anyone any ideas?

---

### Post by taurus on 2008-03-14
Close the update manager.  Then, open a terminal and run these two commands.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by chlorinekid on 2008-03-14
that's alrght for the time being but does anyone know why i'm getting the error? there are still 3 available updates that won't update, getting the same error..

---

### Post by chlorinekid on 2008-03-14
problem solved. /home/root shouldn't even exist. so deleted it and it ran ok

```
sudo usermod -d /root root
```

got the solution from this thread: [http://ubuntuforums.org/showthread.php?t=699130](http://ubuntuforums.org/showthread.php?t=699130)

---

