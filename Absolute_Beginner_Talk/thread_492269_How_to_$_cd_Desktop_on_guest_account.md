---
title: "How to $ cd Desktop on guest account?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-07-04
Hi I can't access the guest accounts Desktop on my pc, even when I'm logged in as 
administrator. when I'm typing in terminal I get the following messages
> rudolf@laptop:~$ cd /home/guest/Desktop
bash: cd: /home/guest/Desktop: Permission denied
And when I'm trying to do it with root privelegies
> rudolf@laptop:~$ sudo cd /home/guest/Desktop
Password:
sudo: cd: command not found
I need to change the permissions for a file on the guest desktop that belongs to root, thats why I need to acces it

---

### Post by Seisen on 2007-07-04
Try```
 sudo -s -H 
``` this will allow you to change to root in the terminal. Then you can go to the directory and change the permissions.

---

### Post by chessercizes on 2007-07-04
hey

whenever i tried running "sudo cd <directory>" i got the same error that you did.


You could run

> gksudo nautilus
to open a root nautilus window which might let you see the files.

Also, you could use the chmod command to change the permissions of the file

> chmod 777 -R /home/guest/Desktop  (to change permissions of all files on desktop)

Im not sure if this is what you're looking for or not, im pretty new to ubuntu too. Hopefully this helps. 

best of luck

---

