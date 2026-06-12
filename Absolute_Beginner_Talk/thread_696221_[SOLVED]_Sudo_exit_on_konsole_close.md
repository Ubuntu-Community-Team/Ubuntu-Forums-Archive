---
title: "[SOLVED] Sudo exit on konsole close"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-02-13
From what my friend told me, the sudo times out after 10 or 15 minutes.

That's peachy 'n all, but I want mine to close when I close konsole.  I don't want to be able to close konsole, then open it back up and sudo still be enabled.

I tried making it so it didn't use a history, but no-go.

I played with the settings, but can't find anything.

Anybody know how?

---

### Post by jaytek13 on 2008-02-13
There is a file for this in /etc/sudoers. In that file you will see a line like this ```
Defaults        !lecture,tty_tickets,!fqdn
``` You can amend the line to add timestamp_timeout=x, where x = the length of time in minutes. So ```
Defaults        !lecture,tty_tickets,!fqdn,timestamp_timeout=1
``` should give you a timeout of 1 minute. 0 will make it so you have to enter in the password every time you use sudo.

Otherwise, as far as just being able to accomplish this "on exit" of konsole, I'm not sure.

---

### Post by Syndacate on 2008-02-14
> **jaytek13 said:**
> There is a file for this in /etc/sudoers. In that file you will see a line like this ```
Defaults        !lecture,tty_tickets,!fqdn
``` You can amend the line to add timestamp_timeout=x, where x = the length of time in minutes. So ```
Defaults        !lecture,tty_tickets,!fqdn,timestamp_timeout=1
``` should give you a timeout of 1 minute. 0 will make it so you have to enter in the password every time you use sudo.

Otherwise, as far as just being able to accomplish this "on exit" of konsole, I'm not sure.

You can't use 0 with scripts - as I just found out, but "1" works, thanks a lot.

---

