---
title: "Enemy Territory and Folder Permissions"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by ToothlessFerret on 2006-10-13
Absolute beginner alert!

Ok, I have installed Ubuntu ok, installed the Nividia drivers ok, but now I want to install Enemy Territory.  Downloaded the file:

mv et-linux-2.60.x86.run.zip et-linux-2.60.x86.run (rename file)
chmod +x et-linux-2.60.x86.run (make executable)
sh et-linux-2.60.x86.run (run installer)

but whenever I try to run the installer, it borks where it tells me that I don't have write permission for /usr/local/games

How do I give myself write permissions for the folder?  I don't have a root or su terminal, and cannot log on as such.  Could someone please give me an idiots guide to resolving this please?

---

### Post by justin whitaker on 2006-10-13
When it gives you the option to chose where it is installed, install it to /home/your name.

---

### Post by skymt on 2006-10-13
You could tell ET to install in a subdirectory of your home directory (that's what I do).

Or, if you want it to be in /usr/share/games, just run "sudo sh et-linux-2.60.x86.run". The sudo command allows you to run a single command as root.

---

### Post by ToothlessFerret on 2006-10-13
Thank you both....  Problem solved as suggested.  I just need to sort out the lack of ET sound next!

---

