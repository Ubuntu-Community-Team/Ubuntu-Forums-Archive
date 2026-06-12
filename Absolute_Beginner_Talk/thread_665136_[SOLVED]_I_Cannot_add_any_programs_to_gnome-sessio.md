---
title: "[SOLVED] I Cannot add any programs to gnome-session"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Promaster91 on 2008-01-11
Hi I am new to Ubuntu. I was adding gdesklet to my startup programs and it won't save it every time i closed the window. Then i ran gnome-session-properties in the terminal and try to add it but it comes back with this.
```

** (gnome-session-properties:6550): WARNING **: Could not save /home/stefan/.config/autostart/gdesklet.desktop file

```
Does anybody know whats going on and does anybody have a solution?

Thanks.

---

### Post by dcstar on 2008-01-12
> **Promaster91 said:**
> Hi I am new to Ubuntu. I was adding gdesklet to my startup programs and it won't save it every time i closed the window. Then i ran gnome-session-properties in the terminal and try to add it but it comes back with this.

** (gnome-session-properties:6550): WARNING **: Could not save /home/stefan/.config/autostart/gdesklet.desktop file

Does anybody know whats going on and does anybody have a solution?

Thanks.

Your .config directory should be owned by your user name, check that it (and all things below it) have the right permissions.

---

### Post by Promaster91 on 2008-01-12
I looked at my ".config" file and I am the owner but it still comes up with the error messge:

```

** (gnome-session-properties:8287): WARNING **: Could not save /home/stefan/.config/autostart/gdesklet.desktop file

```

---

### Post by geirha on 2008-01-12
Could you paste the output of these commands? ```
ls -ld ~/.config/autostart
ls -l ~/.config/autostart/*.desktop
```

---

### Post by Promaster91 on 2008-01-12
ok here is the output

```

stefan@stefan-laptop:~$ ls -ld ~/.config/autostart
-rwxrwxrwx 1 stefan root 189 2007-12-03 21:40 /home/stefan/.config/autostart
stefan@stefan-laptop:~$ ls -l ~/.config/autostart/*.desktop
ls: /home/stefan/.config/autostart/*.desktop: Not a directory

```

---

### Post by geirha on 2008-01-12
The output here says that autostart is a file, while it should be a directory, move away the file, and try adding something to your session again:
```
sudo mv ~/.config/autostart ~/.config/autostart_weird
```

---

### Post by Promaster91 on 2008-01-12
Thank You. It works now. :)

---

