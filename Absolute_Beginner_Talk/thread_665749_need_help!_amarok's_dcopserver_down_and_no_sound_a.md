---
title: "need help! amarok's dcopserver down and no sound at all..."
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2008-01-12
while was using amarok and totem i shutdown by mistake the computer(wanted to lockscreen..wrong button)

the next time i started amarko i had a dcopserver error and no sound generally at all....
not even from other programms....

any ideas?

---

### Post by PeterJS on 2008-01-12
Open up a terminal and try and start the dcopserver manually with the command:
```

dcopserver

```
This should print out an error message as to why the dcop server won't start. The most common reason is that the lock from the server tht got killed still exists, so the server doesn't start, because it thinks it's already running. There are two locks, there are named:
.DCOPserver_*Hostname*__0
and
.DCOPserver_*Hostname*_:0
so if you run:
```

rm .DCOP*

```
and then log out and back in it should clear itself up.

---

### Post by someoneouthere on 2008-01-12
ok done it but when i relogged in all the gnome was kind of sifunctioning... so i reboot...
then everything seems to be ok except i dont have any sound...

---

### Post by PeterJS on 2008-01-12
If you're not getting DCOP errors, then at least that much is fixed. Does the mixer give you any error messages if you try to turn the volume up?

---

### Post by someoneouthere on 2008-01-12
> **PeterJS said:**
> If you're not getting DCOP errors, then at least that much is fixed. Does the mixer give you any error messages if you try to turn the volume up?

nope...

---

### Post by ajmorris on 2008-01-12
re run sudo alsaconf
then run alsamixer and see if it helps....
also, you may need to modprobe the name of the sound driver you are using (if you need help with that, tell us what alsaconf says as the card it picks up, when you run sudo alsaconf)

---

