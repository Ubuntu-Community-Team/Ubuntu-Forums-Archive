---
title: "Starting Gnome from tty"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by nbpetts on 2006-05-04
Sometimes when i do a ctrl+alt+backspace to restart gnome, it just goes to the tty interface.  there is nothing in the tty7 space. 

So what i am wondering is this: Is there a way to start gnome manually?  I have searched quite a bit for this, and i know that it has something to do with startx, but that doesn't quite work, i just get a ruidmentary window system with "startx gnome".  If anyone has a suggestion, that would be very helpful

nbpetts

---

### Post by Sandlst on 2006-05-04
Have you tried ```
gnome-session
```or```
exec gnome-session
```I think one or the other should work....Im blanking on the proper one.

---

### Post by nbpetts on 2006-05-04
i have not tried those yet, but i will.  Thanks a lot.

---

### Post by nanotube on 2006-05-04
or try
```
sudo /etc/init.d/gdm restart
```

---

