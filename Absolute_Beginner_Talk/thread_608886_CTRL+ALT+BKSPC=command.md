---
title: "CTRL+ALT+BKSPC=command?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by mikeserv on 2007-11-10
I'm trying to write a script and I'm wondering if there's a command that will restart X the same way CTRL+ALT+Backspace does.  You know, without a real reboot, but just a reload.

-Mike

---

### Post by tubasoldier on 2007-11-10
```
sudo /etc/rc0.d/K01gdm restart
```
I'm not currently on a debian based distro, so I can't check it for accuracy. But thats basically it. You would have to do it as root or with the sudo command, depending on your script.

---

### Post by mcduck on 2007-11-10
```
sudo /etc/init.d/gdm restart
```

---

### Post by Frak on 2007-11-10
```
gdm-restart
```

That's what it is in Arch, and it shouldn't be any different than in Ubuntu.

---

### Post by ardchoille42 on 2007-11-10
ctrl+alt+backspace is a dirty way to restart x, it doesn't save anything that needs to be saved. You're better off with this:
```
sudo /etc/init.d/gdm restart
```

---

### Post by mcduck on 2007-11-10
> **Frak said:**
> ```
gdm-restart
```

That's what it is in Arch, and it shouldn't be any different than in Ubuntu.

There is no such command in Ubuntu.

"sudo /etc/rc0.d/K01gdm restart" does work, but that is just a link pointing to /etc/init.d/gdm which I, at least, find a lot easier to remember ;)

---

### Post by Frak on 2007-11-10
> **mcduck said:**
> There is no such command in Ubuntu.

"sudo /etc/rc0.d/K01gdm restart" does work, but that is just a link pointing to /etc/init.d/gdm which I, at least, find a lot easier to remember ;)
OK then, alternate way
```
/etc/init.d/gdm restart
```

---

### Post by mikeserv on 2007-11-10
For some reason those don't work.  Instead of restarting back into X, the command seems to just kill X and leave it hanging in between sessions.  You know the black terminal screen that displays things like ```
Running local scripts.... (OK)
```?  That's where it hangs and I have to use CTRL+ALT+DEL to reboot.  But for some reason CTRL+ALT+BKSPC never hangs there.

-Mike

---

### Post by mikeserv on 2007-11-10
Bump.

---

