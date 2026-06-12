---
title: "upgrades won't upgrade"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by terrybob on 2008-02-21
i get this message....????? "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."....uhm...what next please...TR

---

### Post by LaRoza on 2008-02-21
> **terrybob said:**
> i get this message....????? "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."....uhm...what next please...TR

Run this command in the terminal:
```

sudo dpkg --configure -a

```

---

### Post by terrybob on 2008-02-21
thank you sir....now how do i 'run a command in terminal'....us neophites!!!!..thanks again.tr

---

### Post by terrybob on 2008-02-21
i've been through applications, places and system....don't see anything resembling 'terminal'......TR

---

### Post by terrybob on 2008-02-21
oh dear.....messages coming thru as popups....blocked...fixed that for this forum....please resend your messages....thanks mucho....TR

---

### Post by jan de beuker on 2008-02-21
It could also be named konsole.
Ide kde deskrop it is under aplictions > systeem > konsole
Gnome I don't know.
When you still can't find just reboot during the grub menu press escape choose the second option (recovery mode let machine boot at he end you get a terminal type the command there but don't use sudo just the command dpkg --configure -a

Jan

---

