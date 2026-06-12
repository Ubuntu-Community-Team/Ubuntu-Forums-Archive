---
title: "how to turn off notifications?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by emu on 2007-08-01
the notifications that pop up in the top right corner are kind of annoying, in particular, "your battery is fully charged," "power has been unplugged," and "new updates available."  how do I turn these notifications off without removing the icons from the panel?  i.e. I want the battery icon to be there so I have some sense of how much battery life is left, and I want the updates icon there so I can see I have updates but without having it make the annoying popup.  anyone know how to do this?

---

### Post by init1 on 2007-08-01
> **emu said:**
> the notifications that pop up in the top right corner are kind of annoying, in particular, "your battery is fully charged," "power has been unplugged," and "new updates available."  how do I turn these notifications off without removing the icons from the panel?  i.e. I want the battery icon to be there so I have some sense of how much battery life is left, and I want the updates icon there so I can see I have updates but without having it make the annoying popup.  anyone know how to do this?
You can add a different battery charge meter, which I think works better, but there is no substitute for the update icon. You cannot disable the pop ups. I do agree, however, that they are annoying.

---

### Post by asmoore82 on 2007-08-01
I too would be very interested in an official and simple way to turn them off.

for now you/WE can make the notifier daemon unrunnable and kill it ...

```
~$ sudo chmod -x /usr/lib/notification-daemon/notification-daemon 
Password:
~$ killall notification-daemon
```

---

