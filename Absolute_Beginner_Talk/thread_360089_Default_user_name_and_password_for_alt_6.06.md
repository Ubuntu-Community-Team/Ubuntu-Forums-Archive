---
title: "Default user name and password for alt 6.06"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by hub_cap on 2007-02-12
I have installed alt 6.06 Ubuntu and put the bootloader on the root partition. I can boot the program, but am asked for a user name and password. I didn't assign one (that I remember). Is there a default? How do I start the session?

---

### Post by jpeddicord on 2007-02-12
It should have forced you to chose a username. Try using 'ubuntu' for a username and no password. If you cannot figure out what your username is, boot the system in recovery mode (from the GRUB menu) and type the following to see what user you might have installed:
```
ls /home
```If "lost+found" shows up, ignore it. The other listing, however, should tell you the username.

Once you are able to login, you can set your system to auto-login from the System > Administration > Login Window menu.

Jacob

---

