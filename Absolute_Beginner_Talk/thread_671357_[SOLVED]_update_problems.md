---
title: "[SOLVED] update problems ?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Silvain on 2008-01-18
Does anyone know if this is a needed update or is it one I should Ignore?

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb
  403 Forbidden

```

TIA
Silv

---

### Post by atoponce on 2008-01-18
Why are you getting a 403 Forbidden error?  What do you have listed in your /etc/apt/sources.lst file, and what was the command that you used to try and install?

---

### Post by lswest on 2008-01-18
that update is causing xserver problems, and so has been blocked before it causes more troubles

---

### Post by Kulgan on 2008-01-18
> that update is causing xserver problems, and so has been blocked before it causes more troubles

That's good to know. Thought it was slightly odd that I got 403 on a repo server...

:D

---

### Post by JaapJanHellinga on 2008-01-18
I got that error too. How can you fix it, so the Update Manager doesn't show it again as an available update?

---

### Post by Kulgan on 2008-01-18
just wait until the issue is resolved. Once the dev team has fixed whatever broke the update, it will be overwritten on the server and the permissions changed, so that we can install it properly. If you blacklist the package, you won't be able to install it when it's working, so I would just wait until it's fixed.

---

### Post by N2PTF on 2008-01-18
..I'm also getting same error with update manager still saying I have available update as well

---

### Post by zipperback on 2008-01-18
There was a problem found in the package and it was taken down. It will be put back after it is resolved.

- zipperback
:popcorn:

---

### Post by zipperback on 2008-01-18
The problem appears to have been resolved.

as soon as I just issued the following.
```

sudo apt-get update

```

My update manager prompted me about new updates, and it shows a new package is available which is newer than the older broken one.

Wow talk about fantastic response times!

- zipperback
:popcorn:

---

### Post by Kulgan on 2008-01-18
> ..I'm also getting same error with update manager still saying I have available update as well

Just wait. The orange icon isn't that hard to live with. The devs know about it, so it will be fixed soon. Wait a few hours and try downloading the updates again. You can, as far as I know, safely install the other updates that were issued at the same time.

edit:
Thanks zipperback. Beat me to it - was about to reload.

---

### Post by N2PTF on 2008-01-18
Thanks ! I got the update.

---

### Post by nikoPSK on 2008-01-18
it's broken atm. Happens to me too. :)

---

