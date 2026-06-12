---
title: "Run User Account in Sudo with prompt"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by kozmo on 2005-08-21
I'm trying to install Oracle, but certain configuration scripts are failing because they are running under the account that I am logged in as. And because the way Ubuntu is setup it is unable to prefix the SUDO command to these scripts and supply the SUDO password.

The Oracle installer will not allow you to run the installation as root.
 
Is there a way to set up a user account to always run in sudo mode so I can avoid this issue?

---

### Post by aysiu on 2005-08-21
This probably won't help, but did you check out this thread?

[http://ubuntuforums.org/showthread.php?t=16654](http://ubuntuforums.org/showthread.php?t=16654)

---

### Post by nic2 on 2005-08-21
The following link explains how to use "sudo" without prompt for password (not secure)

[http://ubuntuguide.org/#usesudowithoutpasswordprompt](http://ubuntuguide.org/#usesudowithoutpasswordprompt)

---

### Post by kozmo on 2005-08-21
[QUOTE=nic2]The following link explains how to use "sudo" without prompt for password (not secure)

[http://ubuntuguide.org/#usesudowithoutpasswordprompt](http://ubuntuguide.org/#usesudowithoutpasswordprompt)[/QUOTE]

Thanks, but I must have made a typpo when editing the file. Now when I use the sudo command I get that /etc/sudoers has a parsing error. I can't even create a new file and overwrite it because I get a permission error.

How do I get /etc/sudoers back to its original state?

---

### Post by cwaldbieser on 2005-08-21
[QUOTE=kozmo]Thanks, but I must have made a typpo when editing the file. Now when I use the sudo command I get that /etc/sudoers has a parsing error. I can't even create a new file and overwrite it because I get a permission error.

How do I get /etc/sudoers back to its original state?[/QUOTE]
Try booting into recovery mode (see [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) if you are unsure how to do this).  Then you should have permission to correct the file.

---

