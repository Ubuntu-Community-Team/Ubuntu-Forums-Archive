---
title: "opening ports."
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Aximilli on 2007-08-13
So I was hoping I could ssh into my machine while at work, but nmap told me all ports are closed on my xubuntu machine. is there a tutorial somewhere i missed on how to open ports? if not, could someone tell me how?

---

### Post by chriscando on 2007-08-13
Your computer could be behind a firewall (nat router) and that will show all ports as blocked. In that case you will have to configure your router to forward traffic through.

If thats not the case make sure that sshd is running/installed on your machine.
```
sudo /etc/init.d/sshd restart
```

---

### Post by dpar on 2007-08-13
These may help.

[http://ubuntuforums.org/showthread.php?t=524349&highlight=ports](http://ubuntuforums.org/showthread.php?t=524349&highlight=ports)

[http://ubuntuforums.org/showthread.php?t=522950&highlight=ssh](http://ubuntuforums.org/showthread.php?t=522950&highlight=ssh)

---

### Post by Aximilli on 2007-08-13
Ahh, turns out xubuntu doesn't come with ssh installed. Sorry for bothering, i have it working now.

---

