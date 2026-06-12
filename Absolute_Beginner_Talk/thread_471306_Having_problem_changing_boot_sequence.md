---
title: "Having problem changing boot sequence"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by noshdb on 2007-06-11
I want to change the boot sequence, so I need to (I think) change the file menu.lst. But when I try to save the file it gives an error message that I do not have permissions. But the problem is, that I cannot login as root. When I try to login as root I get a message stating that "the system admin is not allowed to login from this session". How can I become the administrator to complete this task?
Thanks

---

### Post by kevinlyfellow on 2007-06-11
Are you in the sudoers file (/etc/sudoers)?

Do you have more than one user account on the machine?

---

### Post by ^Pho[T]on on 2007-06-11
well, there are several thing u can do

goto system -> administration -> login window -> (enter root password) -> goto security tab,
then tick "allow local administrator login". That will allow you to login to pc as the admin

a more sane and efficient way is to go into the terminal and type
"sudo [text editor name eg. gedit] /boot/grub/menu.lst" then enter the root password

sudo allows a permitted user to execute a command as the superuser (ie. as root) or another user, as specified in the sudoers file. (from sudo manual (type "man sudo" in terminal ))

also, u can use "su -" to become root in the terminal. u then start a text editor from the terminal to edit the menu.lst file, eg "gedit /boot/grub/menu.lst" or "nano /boot/grub/menu.lst"

the difference between "su -" and "sudo" is that sudo only executes the command following it as root for that time only, every time u want to execute a command as a super user (root) u can use sudo [command]. "su" on the other hand makes all the commands after that execute as root, until u type "exit" or close the terminal window.

---

### Post by noshdb on 2007-06-11
Thanks Photon. Youre advice helped.

---

