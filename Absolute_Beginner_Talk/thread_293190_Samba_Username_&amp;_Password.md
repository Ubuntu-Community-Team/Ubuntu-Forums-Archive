---
title: "Samba Username &amp; Password"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-11-04
When I connect to my Ubuntu from Windows XP, it asks for a username and password. What are these and how do I know what mine is? Thanks!

---

### Post by bswilson on 2006-11-04
You must create the username and password.  This can be done with the **smbpasswd** command.  Check the man pages for assistance.

---

### Post by amitroy5 on 2006-11-05
How do I do that?

---

### Post by amitroy5 on 2006-11-06
I can't find any info how to do this. How can I?

---

### Post by amitroy5 on 2006-11-06
bump. How can I create a user on samba?

---

### Post by bigken on 2006-11-06
in a terminal type 

sudo smbpasswd -a (your name) 

sudo smbpasswd -e (your name)

your will be asked to create a password ;)

---

### Post by Super King on 2006-11-06
For more details see this link:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server)

---

### Post by adamkane on 2006-11-06
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add.2Fedit.2Fdelete_network_users](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add.2Fedit.2Fdelete_network_users)

---

