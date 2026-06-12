---
title: "su wont work"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2007-12-31
good morning
I am trying to log in as superuser using the su command but here is what happens:

```
simeon@simeon-laptop:~$ su
Password: 
su: Authentication failure
Sorry.
simeon@simeon-laptop:~$ 
```

if I type sudo -s I do log in as a superuser but I dont know what sudo is and why doesnt su work.

BTW i am typing the correct password so the problem is somewhere else.

---

### Post by forestpixie on 2007-12-31
sudo - is the same as su but only works for a specific period of time - at least that how I understand it

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mcduck on 2007-12-31
The problem here is that 'su' asks for the users password you are switching into, in this case root's password. And as there isn't one, you can't use it.. ;)

Use 'sudo' instead, it asks for your own password. And if you don't want to type 'sudo' to every command, use 'sudo -i' to open a root session (and remember to run 'exit' when you don't need to be root any more).

Both 'sudo -s' and 'sudo su' would also work, but they don't load root users environment correctly so you should use 'sudo -i' instead.

---

### Post by rich.bradshaw on 2007-12-31
rather than using su to log in as root, use sudo to do something as root.

i.e.

instead of 

```
su
(Enter Password)
echo "I am root!"
exit
echo "I am me again - I feel so weak."
```

use

```

sudo echo "I am doing this as root"
echo "I'm me again"
```

Means that there isn't a real root user, better for security and it seems neater somehow.

You can run gui apps as root using gksudo

i.e.

gksudo nautilus

will run the file manager as root.

---

### Post by scorp123 on 2007-12-31
> **mcduck said:**
>  Both 'sudo -s' and 'sudo su' would also work, but they don't load root users environment correctly  ```
sudo su -
``` ... The dash "-" after "su" loads the target user's profile.

---

### Post by Sef on 2007-12-31
Read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo") for the differences between sudo and root, and why sudo is better.  (Mostly been covered here by other posters.

---

### Post by b0rka7a on 2007-12-31
Good morning everyone :)
You can change your password by typing:
```
sudo passwd
```

Note: The passwords in Linux are case sensitive!

Edit: I mean your root password ;)

---

### Post by scorp123 on 2007-12-31
> **b0rka7a said:**
> Good morning everyone :)
You can change root's password by typing:
```
sudo passwd
``` This is not a good advice. There is a reason why the root account is disabled. With the root account enabled too many newbies may be tempted to work as root all the time. This is BAD.

---

### Post by fireboy129 on 2008-01-05
> **scorp123 said:**
> This is not a good advice. There is a reason why the root account is disabled. With the root account enabled too many newbies may be tempted to work as root all the time. This is BAD.

i have a similar problem...

i type "sudo su" and i enter my password, but it says that the password is wrong. 

its the right password. any advice?

[EDIT] sorry. error between keyboard and chair.

my fault.

---

