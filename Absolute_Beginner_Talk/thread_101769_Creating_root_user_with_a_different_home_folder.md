---
title: "Creating root user with a different home folder"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by harisund on 2005-12-10
Hello

I installed Ubuntu and I created a user account in the process. However, since for every single customization I need to sudo, I decided to create a root user.

I understand sudo passwd root asks me for a password, and the root account is created. But I don't want the home folder of the root to be /root and instead I want it to be in /home/root. The reason is my /home is mounted on my second hard disk (hdb) and there is space there. 

Is this possible? Or can the root user have a home only in /root ? 

Just curious.. 

Hari

---

### Post by MartinG on 2005-12-10
Have you tried changing /root into a symlink to /home/root?  I don't see why that shouldn't work.

---

### Post by lcg on 2005-12-10
[QUOTE=harisund]I understand sudo passwd root asks me for a password, and the root account is created. But I don't want the home folder of the root to be /root and instead I want it to be in /home/root. The reason is my /home is mounted on my second hard disk (hdb) and there is space there. 

Is this possible? Or can the root user have a home only in /root ? 
[/QUOTE]
Why don't you change root's home in /etc/passwd? I have never done this myself, but I see no reason why it shouldn't work. AFAIK, there are Linux distros out there where root's home is actually /.

HTH,
Lars

---

