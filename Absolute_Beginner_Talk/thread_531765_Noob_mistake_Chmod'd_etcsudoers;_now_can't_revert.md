---
title: "Noob mistake: Chmod'd /etc/sudoers; now can't revert"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Peter108 on 2007-08-21
Wanted to add this line to /etc/sudoers,

myusername ALL=NOPASSWD:/usr/bin/firestarter

to avoid having to provide a password when starting firestarter.  So I chmod'd /etc/sudoers from 440 to 644.  Well, guess what.  Not only am I not permitted to change it back, now every sudo command I enter fails, e.g., 

```
peter@cosmo:/etc$ sudo chmod 0440 sudoers
sudo: /etc/sudoers is mode 0644, should be 0440

```

I'm sure there's a simple way out of this mess, but I'll be damned if I know what it is.

Red-facedly,

---

### Post by lloyd_b on 2007-08-21
Boot the machine in "recovery" mode - this will give you root permissions.  Then do the chmod...

Lloyd B.

---

### Post by pashashome on 2007-08-22
I believe this link should help you.

[http://ubuntuforums.org/showthread.php?t=140852]("http://ubuntuforums.org/showthread.php?t=140852")

Good Luck!

---

### Post by Peter108 on 2007-08-22
Thanks to you both: To Lloyd_b for the recovery mode solution (which worked fine) and to pashashome for the link that led me to the learn about the visudo command.  (Now THAT's a nice-to-know).

---

