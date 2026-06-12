---
title: "display disk usage on startup/login"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by adza on 2007-06-15
hi there, how do i enter the df -a -h command as part of login so that when i login to my server (head only) it displays disk usage stats every time? Thanks :)

---

### Post by 5-HT on 2007-06-15
You could edit /etc/motd to display the required information.
cheers,

---

### Post by reclusivemonkey on 2007-06-15
> **5-HT said:**
> You could edit /etc/motd to display the required information.
cheers,

Isn't motd rewritten every reboot?

Personally, I would add it to ~/.bashrc

---

### Post by adza on 2007-06-15
sweet... thanks monkey! exactly what i wanted... :)

---

### Post by 5-HT on 2007-06-16
> **reclusivemonkey said:**
> Isn't motd rewritten every reboot?

Personally, I would add it to ~/.bashrc

Shouldn't be overwritten, but would need a script in place to update the contents as frequently as desired (a cronjob would be easiest).

---

