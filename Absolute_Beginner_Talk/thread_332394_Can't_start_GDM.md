---
title: "Can't start GDM"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-01-06
I just downloaded a GDM theme and tried to install it. When I went to System->Administration->Login Window (GDM theme), the program didn't start and I don't know why. The only clue I have is because my current login window is KDM. Is it the problem?

What can I do?

---

### Post by tbroderick on 2007-01-06
Is GDM installed?

---

### Post by wersdaluv on 2007-01-06
yes

---

### Post by tbroderick on 2007-01-06
Did you try opening a terminal and running;

```
gksu gdmsetup
```

---

### Post by wersdaluv on 2007-01-06
I just tried it and this is what happened:

```
Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.
```

---

### Post by quartzy on 2007-01-06
To make gdm your login manager this should do the trick:

```
sudo dpkg-reconfigure gdm
```

---

### Post by wersdaluv on 2007-01-06
Okay. So I chose GDM but when I restarted my laptop, it still was KDM and after trying to run Login Window again, it still didn't work.

---

### Post by wersdaluv on 2007-01-06
Thanks! It already works! All I had to do was to reboot my laptop to start using GDM.

Thank you so much!!!

---

### Post by quartzy on 2007-01-06
:)

---

