---
title: "Trouble with Synaptic"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by geovino on 2007-03-07
I'm being asked to login in as superuser and when I do I get this:

davek@davek-desktop:~$ su
Password:
su: Authentication failure
Sorry.
davek@davek-desktop:~$

error: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
I tired and it won't let me because It think I'm not in root but I am in root. How do I fix this?


I had already logged in to use synaptic. earlier something didn't uninstall right and synaptic froze up after that it wanted me to go to the terminal and use this: dpkg --configure -a


How do I get this command to work?

---

### Post by Kateikyoushi on 2007-03-07
To get root permissions use sudo in terminal. [LINK]("https://help.ubuntu.com/community/RootSudo")
```
sudo dpkg --configure -a
```

---

### Post by geovino on 2007-03-07
Thank you !

That's what was needed. Now Synaptic can open again.

---

