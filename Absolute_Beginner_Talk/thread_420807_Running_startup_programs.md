---
title: "Running startup programs"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-04-23
I want to setup this line of code to run at startup> sudo rdate clock-1.cs.cmu.edu && sudo hwclock --systohcThese commands require root priviliges to run. I plan on entering them in /etc/rc.local. Should I include sudo?

---

### Post by simonn on 2007-04-24
> **Patrick K said:**
> Should I include sudo?

No, sudo is unnecessary because the boot scripts are run as root.

However, consider running ntpd. It will keep your time more accurate.

---

### Post by Patrick K on 2007-04-24
Is that the Navel Observatory program?

---

### Post by jfinkels on 2007-04-24
> **Patrick K said:**
> Is that the Navel Observatory program?

I think ntpd stands for Network Time Protocol Daemon. It's a program that will keep your system clock synchronised with a centralized server, whose purpose is only to keep time.

---

### Post by Patrick K on 2007-04-24
Thanks, I set it up and have it running. I gather it stays in sync and doesn't need to be periodically ran manually.

---

### Post by simonn on 2007-04-24
Yes.

---

