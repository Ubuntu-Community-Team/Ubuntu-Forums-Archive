---
title: "Can't remember admin password"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Blind Bob on 2007-04-15
I've been running Ubuntu for about 8 months and haven't used my admin password.Of course I don't remember it now .What or how do I fix this?:confused:

---

### Post by xopher on 2007-04-15
This thread seems to have an answer to your problem ;)

[http://ubuntuforums.org/showthread.php?t=3609](http://ubuntuforums.org/showthread.php?t=3609)

---

### Post by steve.horsley on 2007-04-15
In Ubuntu, your password for admin tasks is just your normal login password. Try that.

---

### Post by Blind Bob on 2007-04-15
Xopher ,I'll try that thanks.
 	
steve.horsley,I tried that and it wouldn't work .

---

### Post by aysiu on 2007-04-15
Then you'll have to reset your password and/or make sure you're in the *admin* group.

First of all, make sure you're in the *admin* group. Type in [the terminal](http://www.psychocats.net/ubuntu/terminal) ```
groups
``` The output should look something like this: ```
bob adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
``` Also, have you edited your /etc/sudoers file lately? If so, you can change everything back to normal by following [this tutorial](http://www.psychocats.net/ubuntu/sudo).

If you really can't remember your password, you can reset it. Reboot your computer. Rather than booting into the regular kernel, press the down arrow and select *recovery mode*. Then type ```
passwd bob
reboot
```

---

### Post by xyrer on 2007-04-16
> **aysiu said:**
> If you really can't remember your password, you can reset it. Reboot your computer. Rather than booting into the regular kernel, press the down arrow and select *recovery mode*. Then type ```
passwd bob
reboot
```

Isn't that a huge security flaw? I mean, anyone can just sit on your pc, reboot and change root password, what about a shared family pc?

---

### Post by aysiu on 2007-04-16
> **xyrer said:**
> Isn't that a huge security flaw? I mean, anyone can just sit on your pc, reboot and change root password, what about a shared family pc?
Read this:
[http://psychocats.net/ubuntu/security#recoveryrisk](http://psychocats.net/ubuntu/security#recoveryrisk)

---

