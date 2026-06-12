---
title: "Ubuntu server - boots into Gnome - can I turn Gnome off?"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Calculator on 2006-09-13
Can I turn Gnome off and on depending when I need to use it?

My Ubuntu Server 6.06 when booted goes straight into Gnome (which is good for a newbie like me).

However, I do not want to allocate server resources to Gnome when the server is running in the background.  Gnome is only good for me when I need somethng more than a command line interface.

Thanks

---

### Post by whizbaby on 2006-09-13
Press *ctrl-alt-F1* to get into console and type

**sudo /etc/init.d/gdm stop**

You restart it by

**sudo /etc/init.d/gdm start**

and pressing *ctrl-alt-F7* to get back to graphics console.

(In console you can still browse the internet with **w3m**)

---

### Post by Calculator on 2006-09-13
Thanks Wizbaby - exactly what I need.

:)

---

