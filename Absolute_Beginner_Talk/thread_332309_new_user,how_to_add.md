---
title: "new user,how to add"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2007-01-05
how do i add a new user to my dapper ,

this will all have to be done from recovery mode as i have lost permissions to my home folder.
so i need to create a new user and transfer everything across

thanks

---

### Post by Bachstelze on 2007-01-05
```
sudo useradd -m username
```

then, if you want to set a password, do

```
sudo passwd username
```

(If you're running from recovery mode, you can omit the sudo since it's running as root)

---

### Post by STREETURCHINE on 2007-01-05
thanks HymnToLife

i got that set up but it wont help me to shift everything like i thought.

is there any way to restore my origanal acc..

if i log in to my origanal acc i have no admin rights ,so no terminal 

i would like to restore that acc(seems i lose permission when i mount hdb1 with 777 permissions)

---

### Post by macogw on 2007-01-05
to copy it, login as the new user and open a terminal.  Type "su" all by itself.  You'll be in there as root.  Now type
cp /home/oldUserName /home/newUserName

Your new account should have admin rights, right?  Go to System > Admin > Users and Groups and you should be able to configure everything from there

---

### Post by Bachstelze on 2007-01-05
*su* will work only if there is a root password set, and is not the recommended way to go in Ubuntu. Instead, edit /etc/group to add the newly-created user to the admin group so it can use *sudo*.

---

### Post by macogw on 2007-01-05
Okay, fine "sudo -s" if you want the whole shell to be root.  I like to avoid typing sudo over and over.  The sudo way:

sudo cp /home/oldUserName /home/newUserName

better?

---

### Post by STREETURCHINE on 2007-01-05
sorry but i have tried it both ways but terminal still tells me 

sudo :must be setuid root

where do i go from here

what is going wrong all i did was mount my second hard drive and again i lose all privlages
on hda1..?

---

### Post by ajmorris on 2007-01-05
if u can manage to get in as root with su or whatever try this:
[PHP]chmod 4111 /usr/bin/sudo[/PHP]

---

### Post by STREETURCHINE on 2007-01-05
> **l337 h4x0r said:**
> if u can manage to get in as root with su or whatever try this:
[PHP]chmod 4111 /usr/bin/sudo[/PHP]

ok i am giving it a try we shall see,willing to try anything to save anouther reinstall

---

