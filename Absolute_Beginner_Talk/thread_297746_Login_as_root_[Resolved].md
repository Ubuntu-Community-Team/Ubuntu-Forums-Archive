---
title: "Login as root [Resolved]"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by gilipter on 2006-11-11
Hello,
When i type sudo, this is what's happening:

marjan@marjan-ubuntu:~$ sudo
sudo: /etc/sudoers is mode 0460, should be 0440
marjan@marjan-ubuntu:~$ 

I guess I changed the /etc/sudoers permissions and now I can't login as root. Synaptic does not work also. Could please someone tell me what is wrong and how to fix this?

Thank you very much!

---

### Post by ReaderRat on 2006-11-11
This should give you root permissions:
```
sudo -s -H
```
Be **careful** how you use it. **[COLOR="Blue"]Back up anything important[/COLOR]**.

---

### Post by gilipter on 2006-11-11
Same thing:

marjan@marjan-ubuntu:~$ sudo -s -H
sudo: /etc/sudoers is mode 0460, should be 0440
marjan@marjan-ubuntu:~$ 

The problem is that I can't start anything with sudo, it displays
sudo: /etc/sudoers is mode 0460, should be 0440

Plaease help

---

### Post by aysiu on 2006-11-11
Reboot into recovery mode and tyep ```
chmod 440 /etc/sudoers
reboot
```

---

### Post by gilipter on 2006-11-11
> **aysiu said:**
> Reboot into recovery mode and tyep ```
chmod 440 /etc/sudoers
reboot
```

Thanks man, that worked
R E S P E C T

---

