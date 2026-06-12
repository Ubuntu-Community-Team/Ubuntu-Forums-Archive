---
title: "New to Ubuntu.. Need to know why SU user is not working."
date: 2005-05-14
forum: Absolute Beginner Talk
---

### Post by Linuxmyatuk on 2005-05-14
How do I enable the SU/ROOT, so that I can add users and groups via the shell.

---

### Post by TravisNewman on 2005-05-14
Ubuntu uses a different system called "sudo"

To add a new user, type in "sudo useradd bob" (obviously replace bob with the username you want to add. It will ask you for YOUR password. The installation adds you to the sudoers file automatically. Any administrative task that requires root access can be done this way. 
I suggest you get used to this system, but if you can't, or just prefer the root account to be active, type "sudo passwd root" in a terminal, enter your password, then it will ask you for the desired root password.
 
There are many various security reasons that sudo was chosen over enabling root, so I'd suggest you give it a good honest try before going to the root account :)
 
Hope everything goes well for you!

---

### Post by Linuxmyatuk on 2005-05-14
Thanks, I will give it a try.. 

Thanks Again. \\:D/

---

### Post by TravisNewman on 2005-05-14
no prob :) welcome to the forums!!

---

