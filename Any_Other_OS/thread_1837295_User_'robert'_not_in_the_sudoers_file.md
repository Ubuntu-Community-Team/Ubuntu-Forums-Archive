---
title: "User 'robert' not in the sudoers file"
date: 2011-09-01
forum: Any Other OS
---

### Post by createdcreature on 2011-09-01
I am trying out Debian, and when I type 'sudo su', it just says I'm not in the 'sudoers' file and this incident will be reported. Any ways to fix this, because "You Don't Own a System unless you can log in as root"!

---

### Post by sanderd17 on 2011-09-01
Just do "su" instead of "sudo su" and you will be asked for the root password.

---

### Post by sisco311 on 2011-09-01
The preferred method for starting a root shell with sudo is: **sudo -i** and with su is: **su -**

@OP:
You have to add your user to the sudoers file.

As root, run:
```
visudo
```
and append the file with:
```

**username**	ALL=(ALL) ALL

```

where **username** is your login name.

If you are not familiar with vi, you can use another editor:
```
EDITOR=nano visudo
```
```
VISUAL=gedit visudo
```

For details, see: **man sudoers** and
[http://wiki.debian.org/sudo](http://wiki.debian.org/sudo)

---

### Post by NightwishFan on 2011-09-01
I am not quite sure but I think you just have to add yourself to the 'sudo' group in System -> Administration -> Users And Groups. Happy Debianing! :)

Edit though as said if you do not have sudo replace it with the below:
sudo = su -c
root = su
gksudo = gksu

If you want to install Debian and have sudo working automatically just leave the root password blank.

---

### Post by sisco311 on 2011-09-01
> **NightwishFan said:**
> I am not quite sure but I think you just have to add yourself to the 'sudo' group in System -> Administration -> Users And Groups. Happy Debianing! :)


I'm not familiar with the default settings in Debian, but yes, if the sudoers file contains a line like **%sudo	ALL=(ALL) ALL**, then adding the user to the sudo group should solve the problem.

**%sudo	ALL=(ALL) ALL** means: allow users from the sudo group to run any command as another user (including root, of course).

---

### Post by NightwishFan on 2011-09-01
> **sisco311 said:**
> I'm not familiar with the default settings in Debian, but yes, if the sudoers file contains a line like **%sudo	ALL=(ALL) ALL**, then adding the user to the sudo group should solve the problem.

**%sudo	ALL=(ALL) ALL** means: allow users from the sudo group to run any command as another user (including root, of course).

Cool thanks. I am glad I was right (I hate giving potentially bad advice).

It says:
```

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL

```

---

### Post by sisco311 on 2011-09-01
> **NightwishFan said:**
> Cool thanks. I am glad I was right (I hate giving potentially bad advice).

It says:
```

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL

```

Good, then the OP only needs to add robert to the sudo group:
```
gpasswd -a robert sudo
```
(log out and log back in)

He might also want to change the authentication mode in **gsku-properties**.

---

### Post by createdcreature on 2011-09-05
OK. Typing 'su' instead of 'sudo su' works really well.

---

