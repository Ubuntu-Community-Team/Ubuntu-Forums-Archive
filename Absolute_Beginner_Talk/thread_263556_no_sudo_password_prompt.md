---
title: "no sudo password prompt"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by handle1790 on 2006-09-23
Somehow I managed to fiddle around enough to disable this accidently.

I've tried googling and all that comes back is about disabling prompts for one specific program :(

To clarify, when I run the terminal and use a sudo command, even sudo -s -H, or sudo  apt-get, it does **not** ask me for a password.  When using the GUIs like update notifier, or firestarter, it does **not** ask me for a password there either.

So the goal is to reeable those prompts.

My only thought was that I had been messing around with chmod and chown.

Thanks much.

---

### Post by Klaidas on 2006-09-23
After you use sudo once, you will not be asked again for about 10-15 minutes.
Then it will reset and you will have to insert your password.

---

### Post by handle1790 on 2006-09-23
There is **never** a sudo pw prompt.

---

### Post by handle1790 on 2006-10-01
fixed it, if anyone was curious

I did pico /usr/group , and added my username to the group "sudo".

This removed the need for passwords for sudo commands.

---

