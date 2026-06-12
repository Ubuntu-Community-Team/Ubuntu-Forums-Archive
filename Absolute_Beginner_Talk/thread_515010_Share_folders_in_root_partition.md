---
title: "Share folders in root partition?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by rstewar on 2007-08-01
Hi, I am completely new to Ubuntu. I just installed it yesterday and I installed Apache. The Apache root directory is on my root partition and I can't write to it unless I am logged in as the Root administrator. Is there a way to make the the Apache root directory available  to other users with full permissions? Thanks in advance for any help.

---

### Post by scrooge_74 on 2007-08-01
I am no  expert, but I dont think you want to give every body access, anyway I think you have to join those users to the Apache group or whatever is called so they can have access to it.

---

### Post by e_james on 2007-08-01
I am also no expert but I remember reading somewhere that that's the way apache works. I think it's something to do with the security aspect of running a web server.

---

### Post by p_quarles on 2007-08-01
I think the confusion here is between the system's root directory and Apache document root directory. 

By default, the doc root is /var/www/  Any .html or .php files in that directory are "served" to a client making an http request on the machine running Apache. 

Personally, I use Webmin to transfer files to the document root from my desktop, but this doesn't work if you want multiple users to have access. 

The safest way to do what you want is to set up that folder as an sftp directory and create a separate user that only has access to that folder. That way, you can safely give out that info to others who need access to that folder, without giving them access to other parts of the system.

---

