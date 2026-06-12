---
title: "Can't import public pgp blocks"
date: 2013-03-12
forum: Any Other OS
---

### Post by Creenome on 2013-03-12
I cannot seem to figure this problem out.
I'm running Mint 13 mate x64, may I remind you this is a fresh install.
I've followed the instructions on the GNUPG site on creating key pairs and importing keys. When I was testing out Mint 14 Mate everything worked as it should have, which brings up my current problem.
Importing GPG key blocks doesn't work.

A copy of my konsole
```
keith@Boss ~ $ gpg --import key.txt
gpg: can't open `key.txt': No such file or directory
gpg: Total number processed: 0
```

key.txt does exist.
running ```
ls
```gives back
```
keith@Boss ~ $ ls key.txt
ls: cannot access key.txt: No such file or directory
```

Help would be appreciated

---

### Post by Perfect Storm on 2013-03-12
Moved to Other OS/Distro Talk.

---

### Post by Cheesemill on 2013-03-12
Can you post the output of...
```
ls -lha ~
```

---

