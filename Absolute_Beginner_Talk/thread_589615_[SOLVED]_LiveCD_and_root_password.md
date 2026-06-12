---
title: "[SOLVED] LiveCD and root password"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by emn8w8 on 2007-10-24
Hi,

I want to see what Ubuntu is before installing it. So i'm using the LiveCD. But i do need to perform some tasks (mounting disk partitions is the most important)  as root and do not have root's password in this situation. Where can i find it?

Thanks, Erik

---

### Post by MegaJim on 2007-10-24
Use "sudo" instead of logging into root with "su", e.g. to mount something

```
$ sudo mount -a
```

it shouldnt ask for a password

---

### Post by mojoman on 2007-10-24
> **emn8w8 said:**
> Hi,

I want to see what Ubuntu is before installing it. So i'm using the LiveCD. But i do need to perform some tasks (mounting disk partitions is the most important)  as root and do not have root's password in this situation. Where can i find it?

Thanks, Erik

Two options. You could (1) use the command 'sudo' before every root command (which will execute it as root) without asking for a password (on the LiveCD only, otherwise, password is required) or, if you tire of writing sudo, you can type in 'sudo passwd root' and it'll prompt you for a root password. Type it in, repeat it, and then type 'su' to switch to root user (this password will expire after you reboot as it is only in the RAM).

/mojoman

---

### Post by earobinson on 2007-10-24
Best way to gain root access: ```
suod -s
```

---

### Post by steve.horsley on 2007-10-24
Roots passwordid disabled in Ubuntu, so you have to use sudo instead. Open a command prompt and enter the command
**sudo -i**
This gives you a root prompt.

[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by emn8w8 on 2007-10-24
MegaJim, MojoMan: Thank you very much..!

Erik (who's going to evaluate Ubuntu in depth now..)

---

### Post by emn8w8 on 2007-10-24
And thanks to all other helpers of course...

Erik (who is a bit ashamed because he overlooked the obvious...:-))

---

