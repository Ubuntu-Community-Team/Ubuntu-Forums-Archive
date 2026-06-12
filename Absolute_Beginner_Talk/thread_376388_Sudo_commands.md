---
title: "Sudo commands?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Jowe on 2007-03-04
Is there any way to make your own sudo commands? Just curious :D

---

### Post by 23meg on 2007-03-04
Can you clarify what you mean; what exactly are you looking to do? You can use sudo with practically every command to execute it as root.

---

### Post by moshuptrail on 2007-03-04
Sure!

Any linux command can be run by preceding it with sudo.

The sudo prefix is merely a command that executes the following command as root.
So you can type: sudo <any command>

Furthermore, the command could be a shell script that you write!  look up bash and linux commands.

---

### Post by freeflyer57 on 2007-03-04
sudo stands for super user do. Therefore, sudo does anything, but not everything needs root permission.

---

### Post by glotz on 2007-03-04
One word of caution, use sudo to run text based apps and gksudo to run graphical apps. Otherwise you might end up with a nasty permissions SNAFU.

---

