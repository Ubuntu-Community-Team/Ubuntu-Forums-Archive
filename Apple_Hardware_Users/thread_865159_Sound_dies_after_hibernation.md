---
title: "Sound dies after hibernation"
date: 2008-07-20
forum: Apple Hardware Users
---

### Post by hanzomon4 on 2008-07-20
pavucontrol shows all of the various apps outputting sound but I can't hear any thing. The whole system is effected, audio players, notifications, skype, everything. Some things like audio players behave fun, I press play at it stays at zero. Skypetest call reports no sound errors but doesn't actually start the call.

I've checked the volume sliders, restarted alsa, restarted pulse, unloaded and reloaded snd-hda-intel... Nothing. however trying to run sudo pactl load-module module-x11-xsmp (which is in the session startup) fails. I believe the problem lies in this... So take it away UF

---

### Post by hanzomon4 on 2008-07-23
Ba bump

---

### Post by cyberdork33 on 2008-07-24
> **hanzomon4 said:**
> however trying to run sudo pactl load-module module-x11-xsmp (which is in the session startup) fails. I believe the problem lies in this...
Not much help, I know, but just FYI, that command fails for me in a running VM system that I have access to right now as well... I think it will even if your sound was working...

```
cyberdork33@Ubuntu-Virtual:~$ sudo pactl load-module module-x11-xsmp
Failure: Module initalization failed
```

---

### Post by hanzomon4 on 2008-07-24
I'll check it out, it's in the default session though.

---

### Post by cyberdork33 on 2008-07-25
> **hanzomon4 said:**
> I'll check it out, it's in the default session though.
It might execute fine if it has not already been executed, but it does definitely fail when sound is working for me.

---

### Post by hanzomon4 on 2008-07-27
Yup fails.... this is so weird of an issue

---

