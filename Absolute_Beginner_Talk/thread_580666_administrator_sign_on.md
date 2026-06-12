---
title: "administrator sign on"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by walker81 on 2007-10-19
I have successfully installed Ubuntu several months ago on a spare drive for my laptop. I put the drive in tonight and started the machine it loads up fine and takes my sign on and password fine. I really like it compared to windows. My problem is I cannot do any of the administrator stuff such as add or remove programs or install up dates etc. I cannot remember ever setting up an administrator password. What do I do now to do these items that are administrative.

Thanks in advance for your help

---

### Post by JTux on 2007-10-19
Administrator password is the same password you set for the first user account

ie If you have only one user account then admin password is the password of that user

---

### Post by John.Michael.Kane on 2007-10-19
You should be able to use sudo to get things done. 

example:
gksudo aptitude install xyz program upon which you should be asked your pass. Which would be the same one you used to log in with.

---

