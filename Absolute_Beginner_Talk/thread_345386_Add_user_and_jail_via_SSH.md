---
title: "Add user and jail via SSH?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by iluminate on 2007-01-24
Hi all,

Does anyone know how to jail a user to a specific folder? 
In this case its /var/www/htdocs/templates/  
I can not figure it out...do I have to set the above direcotry as her homedirectory or what?

Is this correct -
sudo adduser lena --base-dir /var/www/htdocs/templates/ 
What is the difference between basedir, homedir?
Any help please would be appriciated!

---

### Post by LotsOfPhil on 2007-01-24
Not a full answer, but I believe what you are trying to do is called chroot

---

