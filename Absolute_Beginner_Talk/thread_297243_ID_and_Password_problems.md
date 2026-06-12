---
title: "ID and Password problems"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by strath on 2006-11-10
I set up new passwords for user and admin removed oem after setting up as oem, then when I restarted, I had lost all access to administrative functions, including Synaptic; System preferences and System Admin reduced to basic. I still have my saved oem desktop but have no administrative access. Can't get in through terminal. Do I have to re-install and start over? (Version 6.06.1)

---

### Post by taurus on 2006-11-10
Boot into recovery mode and add that user to groups adm & admin in /etc/group.

```
nano -Bw /etc/group
```

---

### Post by strath on 2006-11-10
I tried to log in through the recovery mode, as well as as via the regular modes, but no matter who I ID'd myself as I could not get in. I can get into any of my ID's with the appropriate passwords, but whenever I try Synaptic, it says not logged in as root so I can only use as Read Only. I know enough about Linux to know that I must update regularly.

---

### Post by taurus on 2006-11-10
When you boot your machine to the recovery mode, you don't need to log in because you are in as root!  Then, just add your username to both groups adm & admin in /etc/group from the prompt!

```
addgroup <username> adm admin
```

---

