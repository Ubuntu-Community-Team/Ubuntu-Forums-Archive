---
title: "Changing System Files?"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by Phuayj on 2005-12-14
How can I edit the system files(I know what am I doing)?

---

### Post by psusi on 2005-12-14
Could you be a bit more specific?

If you mean what program can you use to edit files, I usually use either pico or emacs.

If you mean how do you get permission to write to a certain file, then prefix the command with sudo to run the command as root.

---

### Post by Phuayj on 2005-12-14
[QUOTE=psusi]If you mean how do you get permission to write to a certain file, then prefix the command with sudo to run the command as root.[/QUOTE]

This is what I meant.

---

### Post by aysiu on 2005-12-14
Let's say you want to edit /etc/apt/sources.list
Just open a terminal and type ```
sudo nano /etc/apt/sources.list
```

---

