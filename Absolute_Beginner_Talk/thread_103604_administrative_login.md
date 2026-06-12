---
title: "administrative login"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by RBH on 2005-12-14
ok, i may have screwed up installing. for some reason i cannot install things, so i looked through alot of settings and see that i am not in a group allowed to write to the root which i imagine is what keeps me from creating directories to install things. i dont recall during setup getting asked about an admin type account. is there a default username password for the admin account or do i need to just go back through the install?

---

### Post by 23meg on 2005-12-14
The root account is disabled by default. Did you try using [sudo]("http://wiki.ubuntu.com/RootSudo")?

---

### Post by lreyes6 on 2005-12-14
i don't know if i'm giving you a gun to give yourself a shot but you can set a root password this way:
in the command line write this
```
sudo passwd root
```
then will ask for your passord (your user password) 
then will ask for te NEW root password and for u to CONFIRM it

you can read [this]("https://wiki.ubuntu.com/RootSudo") too

---

### Post by RBH on 2005-12-14
ok, i set all that but i still cant do anything. when i try and install a simple program like acrobat eader i get to the part where it asks me to install in a directory. i try everything and it just says access denied. i am sure it is something easy that i am not doing but i can figure it out.

---

### Post by RBH on 2005-12-14
not wanting to change root password, just wanting to give my user account the permissions to install things. maybe i am just doing something wrong and it has nothing to do with my user account. hmmmmmmmmmmmmmmmmmmmmmm, i will play around some more thanks

---

### Post by 23meg on 2005-12-14
You need to put "sudo" as a prefix to the command you use to create directories (outside your home directory) or install programs. How exactly do things fail when you do that? What errors are you getting? Noone can help without knowing exactly what the symptoms are.

---

### Post by Micro Rotors on 2005-12-14
up in the top toolbar  .....  **System**>>**Administration**>>**Users and Groups**

---

### Post by RBH on 2005-12-14
ok, this is what happens when installing acrobat reader. i run the install from a terminal. i get this

"Enter installation directory for Acrobat 5.0.10 [/usr/local/Acrobat5]"

i try using their default, /usr/local/Acrobat5, and i have tried using /acrobat5. 

whatever i do gets this response

 "Directory "/usr/local/Acrobat5" does not exist.
Do you want to create it now? [y]"

i hit enter and then this happens.

mkdir: cannot create directory `/usr/local/Acrobat5': Permission denied

ERROR: Cannot make directory "/usr/local/Acrobat5".

---

### Post by 23meg on 2005-12-14
What command do you run the installer with? Did you try appending "sudo" as a prefix to that command?

---

