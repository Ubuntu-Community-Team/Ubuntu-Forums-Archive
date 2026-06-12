---
title: "su/ sudo command fails"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by geo_bio on 2006-10-25
I type in "su" (w/o quotes) in order to get admin powers. It asks for a password, and I type in the password that I use to log in, and to access everything from the administration and preferences panel (top left).

After I type in my password, it seems to fail and say that it doesnt work.

However, when I type in a command such as "sudo cd /home/account/file.lst /home/boot/grub", it asks for the password and works fine.

Can you explain why I can't just use "su" in order to gain admin access to everything without typing the password each time?

---

### Post by prof_booty on 2006-10-25
try 'sudo -s' to get persistent root privleges

the root account is disabled by default in Ubuntu, a security measure.  however, i believe sudo remembers your password for 5 minutes after you enter it, so there is rarely need for a persistent root session.

---

### Post by geo_bio on 2006-10-25
Thanks, it does help.

However, it just seems odd since my previous installation of Ubuntu (before it failed to start up) would accept the "su" command.

---

### Post by CatKiller on 2006-10-26
**sudo** uses your password. **su** uses the (inaccessible by default) root account's password.

If you switch to root, anyway - you can use su to switch to any user.

---

