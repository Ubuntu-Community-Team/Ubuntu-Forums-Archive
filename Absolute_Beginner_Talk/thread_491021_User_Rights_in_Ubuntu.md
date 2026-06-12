---
title: "User Rights in Ubuntu"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by StuNick on 2007-07-03
Help, I am new to Ubuntu and Linux
I have installed Ubuntu 7.04 and it asked me for a user name which I entered but this user doesn't have the rights to do certain things like print to /dev/usblp0 or write to the etc/x11 dir
I will need to instal an application on this box later and have a user id that needs to be able to print and run the application
Is there such a thing as a power user, I don't want to use root as everyone tells me that is a bad idea.
Thanks

---

### Post by meborc on 2007-07-03
don't use root... use sudo...

more info here - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

to keep linux safe from viruses, default user has limited actions... to have access to all actions, sudo must be used...

---

### Post by GeeZor on 2007-07-03
sudo passwd root

(enter the password for the user)
enter the new password for root
again

su - root
give root password.


GOD MODE ON

---

### Post by meborc on 2007-07-03
be careful... it is STRONGLY ADVISED not to change the root password... read the link i gave you instead...

if "sudo" is not "strong" enough for you, you can gain the root privileges with the command ```
sudo -i
```and entering your normal password...

root password is hidden by default in ubuntu and for safety reasons it is advised NOT TO CHANGE IT

there are many threads about changing the root password and then forgetting it after a while... be careful ;)

---

