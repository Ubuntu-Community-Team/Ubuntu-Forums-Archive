---
title: "Change Hostname, System down"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by David C on 2007-07-26
Hey all, 

Newly converted Ubuntu user here.

I think I've made a very big boo-hoo. I've changed my hostname on my terminal from "Grimlock" to "grimlock" via the command:

```
sudo hostname grimlock
```

Now, after I close my terminal, I can't logon my terminal anymore. It showed me an "Starting Terminal" on my taskbar and that's it. After that, it disappears and that's it.

My GAIM conversations, on the taskbar, now has an additional "<nick of person i'm talking to> (on Grimlock)"

How can I revert it :(

---

### Post by scxtt on 2007-07-26
there's also an /etc/hostname file that should be changed, and you should probably check out /etc/hosts to see if it uses g or G (and update accordingly) ... you may need to reboot to totally update it, not sure ...

---

### Post by David C on 2007-07-26
Problem is, I can't access terminal or any application to edit my /etc/hosts

:(

---

### Post by scxtt on 2007-07-26
what about **gksudo gedit** or something like that? -- and you can always boot into recovery mode and do whatever you need to do ... i've changed my hostname and have been in the same predicament as you, it's not permanent ;)

---

### Post by David C on 2007-07-26
How do I run gksudo gedit, without terminal?

---

### Post by scxtt on 2007-07-26
alt+f2 ... suppose i forgot to mention that ;)

---

### Post by David C on 2007-07-26
> **scxtt said:**
> alt+f2 ... suppose i forgot to mention that ;)

Thanks :)

Tried it, nothing happens after I typed in "gksudo gedit". Even "sudo hostname grimlock" does nothing.

Tried running both of them in Terminal and non-terminal on "Alt-F2"

---

### Post by scxtt on 2007-07-26
i'd reboot into recovery mode, then as root (automatically will be root) edit /etc/hostname and /etc/hosts to how you want them ...

---

### Post by David C on 2007-07-26
Thanks again.

How do I get to recovery mode?

---

### Post by David C on 2007-07-26
Ignore me.

I rebooted, and for some reason, everything works again :-)

So what's the proper way to changing a hostname?

---

### Post by scxtt on 2007-07-27
all i ever do is make sure my LAN ip is defined fully and /etc/hostname contains the name i want ... i think the network manager (system --> administration --> network) can set it too ...

/etc/hosts:
192.168.1.100 grimlock.localdomain grimlock

/etc/hostname:
grimlock

---

