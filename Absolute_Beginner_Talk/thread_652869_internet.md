---
title: "internet"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by arvindenrique on 2007-12-29
[SIZE="3"]should i use SUDO PPPOECONF cmd everytime 2 connect 2 internet?[/SIZE]

---

### Post by Joeb454 on 2007-12-29
it depends how you connect to the internet...do you use a USB Modem or a Router with an Ethernet cable?

Also, your font was a bit big for the forum :)

---

### Post by aktiwers on 2007-12-29
If that is what you need to do, just add it to the Session. Its under
System => Preferences => Session

Then it will do automatically on startup.

Or place the command in /etc/rc.local
```
sudo gedit /etc/rc.local
```

Then It will run on start up!

---

