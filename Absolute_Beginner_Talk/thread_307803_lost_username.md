---
title: "lost username"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by MySweetTedy on 2006-11-27
Hi, just reinstalled ubuntu 6.10 but i dont remember entering username, and now at login it asks me for a username, i know what password i wrote but now i am kinda lost in ubuntu login screen, i am at recovery mode and if some1 tell me what to write there to fix the prob would be very greatful

---

### Post by steve.horsley on 2006-11-27
Go into recovery mode, and look at the contents of /home. (ls /home). Alternatively look at the contents of /etc/passwd (less /etc/passwd). Both will contain your username, but /etc/passwd contains lots of other users too.

---

### Post by MySweetTedy on 2006-11-27
10x works username was OEM

---

### Post by bapoumba on 2006-11-27
Then just **sudo oem-config-prepare**. Next time you'll reboot your computer, the oem user will be deleted, and you'll be prompted to create a new user login and password :)

---

