---
title: "maintenance password?? What the?"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Budgi on 2006-09-04
Ok, i have a problem where i need to change the host and hostname records but I cant through sudo because it wont start the administration applications. Problem is when i log in to recovery I get a request for a maintenance password? What is this and is there a standard default one. 

By the way I have gone past it and tried changing the password but it wont let me save the changes

Please help.

Thanks Guys.

---

### Post by Uluen on 2006-09-04
This sounds like your Windows admin password :)

---

### Post by 3rdalbum on 2006-09-04
If you have enabled the root account in the past, then the maintanance password is the root password.

You may find that you still can't access the programs from Recovery Mode to change your hostname back. The hostname file is located in /etc/hostname.

Don't worry, you're not the first to have changed their hostname without knowing the consequences :-)

---

