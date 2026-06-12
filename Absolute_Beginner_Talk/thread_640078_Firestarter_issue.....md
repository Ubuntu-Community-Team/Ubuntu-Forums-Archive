---
title: "Firestarter issue...."
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by nikolas68 on 2007-12-13
I've had Firestarter working for months with no issues: this morning i've decided i wanted to have it starting on booting....did that in System>Preferences>Sessions and add it on start up and also changed the /etc/sudoers so that wouldn't ask for password.
ALL was good for a minute but then a message said that Firestarter stopped working. Try to launch it again....but nothing happens. Opened a terminal and did sudo firestarter: it works....but when i close the terminal Firestarter closes itself.
Then i'm thinking that it's probably running in the background....opened a terminal did top but it's not there!!!! Tried to uninstall and reinstall...same issues...
ANY IDEA!!!!  :confused:

thanks

---

### Post by Dr Small on 2007-12-13
Try:
```
ps aux | grep firestarter
```

But for your knowledge, Firestarted doesn't need to be running, to have your firewall running. Firestarter is the graphical user interface for configuring your firewall, iptables.

Dr Small

---

### Post by nikolas68 on 2007-12-13
> **Dr Small said:**
> Try:
```
ps aux | grep firestarter
```

But for your knowledge, Firestarted doesn't need to be running, to have your firewall running. Firestarter is the graphical user interface for configuring your firewall, iptables.

Dr Small

Thanks....but i don't understand what i'm getting...

```
nicola@ubuntu:~$ ps aux | grep firestarter
nicola    7654  0.0  0.0   2976   764 pts/0    R+   09:59   0:00 grep firestarter
nicola@ubuntu:~$ 
```

---

### Post by Dr Small on 2007-12-13
That is just showing you, that the only thing running the word "firestarter" was grep itself. So, that means there was no firestarter instances running.

---

### Post by nikolas68 on 2007-12-13
...so what to do? i've run out of ideas!

---

### Post by Dr Small on 2007-12-13
Have you tried removing Firestarter from the startup sessions, and then rebooting ?

---

### Post by nikolas68 on 2007-12-13
Why if i uninstall, reboot and reinstall it's still maintaining the previous settings? id there a way around?

---

### Post by nikolas68 on 2007-12-13
> **Dr Small said:**
> Have you tried removing Firestarter from the startup sessions, and then rebooting ?

yes..

---

