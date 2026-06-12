---
title: "trying to get root"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by gpw1 on 2006-08-07
HOWTO: Install Cups-PDF
I was trying to use this HOWTO; and was instructed to go to terminal and type "sudo nautilus". After doing this my computer just sits with blinking cursor.
I think that I'm suppose to get root, but it just sits there blinking.

gpw1

---

### Post by Apple 101 on 2006-08-07
You should type *gksudo nautilus* or *gksudo nautilus <folder location>*

---

### Post by Jagot on 2006-08-07
That command is trying to launch the file browser as root.  It should be gksudo nautilus instead.  If you need to be root the read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by gpw1 on 2006-08-07
This is the results I get...

george@george-laptop:~$ gksudo nautilus
(nautilus:8765): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


gpw1

---

