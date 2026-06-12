---
title: "how to add commad to startup script?"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by IngFreeman on 2006-10-28
what is the correct way to add a command to startup script of ubuntu edgy?
thanks

---

### Post by happy-and-lost on 2006-10-28
System-->Preferences-->Sessions--->Startup Programs

---

### Post by IngFreeman on 2006-10-28
> **happy-and-lost said:**
> System-->Preferences-->Sessions--->Startup Programs

don't works!

my command is: sudo setpci -s 06:06.3 4c.b=02

---

### Post by David_T on 2006-10-28
To add a script that runs at startup, just add whatever you want to /etc/rc.local.
That's what I do for loading my iptables settings and it works great.

(edit:  btw you don't have to use sudo in rc.local, it will be run as root)

---

### Post by IngFreeman on 2006-10-29
> **David_T said:**
> To add a script that runs at startup, just add whatever you want to /etc/rc.local.
That's what I do for loading my iptables settings and it works great.

(edit:  btw you don't have to use sudo in rc.local, it will be run as root)

It works great for me too! :D 
Thank you very much ;)

---

### Post by spamzilla on 2006-10-29
What would i need to type into this file to get gaim to startup when I reboot my system?

---

### Post by mozetti on 2006-10-29
**spamzilla** - Use this method:

> **happy-and-lost said:**
> System-->Preferences-->Sessions--->Startup Programs

---

