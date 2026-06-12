---
title: "Can't shut down!"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-11-09
I recently changed my GDM login window and my theme, and now for some reason the "log out" or power button, whatever you wanna call it, doesn't have "shut down" or "restart." I tried logging out, but the GDM login window doesn't have those commands anymore, either. I had to go into the terminal and type "reboot" to see if that would help, but it didn't. How do I fix this?

---

### Post by punx45 on 2006-11-09
```
sudo shutdown -r now
```
the -r tells it to reboot after if you want.   drop the -r if you just want it off.

---

### Post by Ben Sprinkle on 2006-11-09
Go in the admin panel thing->Change login theme->Choose another and it will.
Just mutate it to your liking, it will fix your issue.

---

### Post by bulldog on 2006-11-09
Go to system--management--login screen and turn on the action menu.
[think it's called that way,first tab anyway]

---

### Post by kbsuperstar on 2006-11-09
Thanks, I'll try it out.

---

### Post by kbsuperstar on 2006-11-09
It worked! Thanks, bulldog :)

---

### Post by bulldog on 2006-11-09
Nice.

---

