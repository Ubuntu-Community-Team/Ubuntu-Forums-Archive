---
title: "SMB server"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2007-10-11
I am setting up a smb server and while trying to run this command i get this error message any ideas?

:# net groupmap modify ntgroup="Domain Admins" unixgroup=root

NT Group Domain Admins doesn't exist in mapping DB


Thanks again

---

### Post by docshawnc on 2007-10-11
just a question - does the Admin group exist when you look for it via the users/groups menu?

---

### Post by poordamnedfool on 2007-10-11
I dont know, this is my first time setting up a file server and i am trying to patch things from different wilkis to put it together.

---

### Post by docshawnc on 2007-10-11
Have a look here - it's a step-by-step to get smb running and assign various permissions - it might be what you need

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

---

### Post by poordamnedfool on 2007-10-11
Thanks will give it a try

---

### Post by nebid on 2008-02-10
I found these groups disappeared in 7.04 (though it may have been deleted when i deleted all the samba users created when apt installed samba).

You can add it with the following line:

net groupmap add rid=512 ntgroup="Domain Admins" unixgroup=staff type=d

---

