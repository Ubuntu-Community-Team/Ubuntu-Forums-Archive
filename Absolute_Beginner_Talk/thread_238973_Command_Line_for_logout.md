---
title: "Command Line for logout?"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by Dinerty on 2006-08-18
Installed GDesklets and have found the commands to shutdown and reboot,

sudo shutdown -h now = Shutdown

sudo shutdown -r now = Reboot

But cant find the one to "Logout?"

---

### Post by Klaidas on 2006-08-18
If you're in, say, recovery mode and you login as a user, you can use > logout
Or was it > exit Don't really remember :)

As for logging out using terminal in a GUI - don't know.
But why would you want to do it? Isn't System > Quit -> Logout faster than opening terminal ant typing a command? :)

---

### Post by anilc on 2006-08-18
Try "halt"

---

### Post by waldschm on 2006-08-18
Doesn't halt completely shut down rather than just logout?

---

### Post by Arisna on 2006-08-18
> **waldschm said:**
> Doesn't halt completely shut down rather than just logout?
Yes, it does.

---

### Post by pbaehr on 2006-08-18
> **Klaidas said:**
> If you're in, say, recovery mode and you login as a user, you can use 
Or was it  Don't really remember :)

As for logging out using terminal in a GUI - don't know.
But why would you want to do it? Isn't System > Quit -> Logout faster than opening terminal ant typing a command? :)

It's just 'logout'

'exit' is for closing a terminal window.

And for what it's worth, conveniently, ctrl+d works as a shortcut for both of those commands.

---

### Post by kepos on 2006-08-18
if you use ubuntu without desktop then command is 'exit'

---

### Post by LadyDoor on 2006-08-18
GNOME isn't always the most user-friendly when it comes to providing command-line alternatives...

---

### Post by UltraMathMan on 2006-08-18
If you just need to run something as another user you could always use ```
sudo -u *username*
```

---

### Post by space_man on 2007-07-02
who -u shows all the users and all their processes (pid's)
the first pid beside the username is that users session.

type kill and that pid to kill their (or your) session.
this takes you back to the logon screen.

---

### Post by phizikal on 2007-07-02
CTRL+ALT+Backspace?

I think?

---

