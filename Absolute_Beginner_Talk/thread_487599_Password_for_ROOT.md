---
title: "Password for ROOT"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by gheywood on 2007-06-29
During installation, I created an account as directed, and set a password. However, is there a seperate ROOT account? if so, what is the password?

This is on a server installation of 7.04.

Cheers

---

### Post by darkrose on 2007-06-29
There isn't a root account by default, you can work as root with:
sudo -s

or enable root by setting a password for the root account:
sudo passwd

which is what I always do on my servers.

---

### Post by gheywood on 2007-06-29
Thanks. The reason I was asking, is for the VMWare management console. When I logon, using the account created, it tells me that I don't have permissions to adjust the server options. I guess there will be a work around for it though.

Cheers

---

### Post by Tomosaur on 2007-06-29
There is a seperate root account, but it is disabled by default. If you want to use root permissions, you use the 'sudo' command, like so:

```

sudo nano /etc/apt/sources.list

```

The password it asks for is your own user password, but you will not see it being typed, so be sure to spell it correctly.

If you stll want to enable the root account, you can do so by typing:
```

sudo passwd root

```
If you are not already logged in to sudo (it will keep you logged in for about 15 minutes, but you still need to use the sudo command otherwise it will assume you want to perform your task as an ordinary user), then it will first ask you for your own password, then you can set the root password.

It is not reccommended that you do this, however - an attacker knows that a root account exists, so they only have to guess a password. If root is disabled, then they have to guess both a username which is capable of using sudo (and only the very first account created in Ubuntu is capable of this, subsequent ones have to be given permission to use sudo explicitly), and that user's password.

However, it is of course up to you :)

---

### Post by gheywood on 2007-06-29
Thanks. It is an internal box so I am not *too* concerned about it. 

I guess I have two choices. Enable the root as you say, or change the 1000's to 0's in the passwd file. I suppose the second option is perhaps better in that the root is still disabled?

I guess the next step is to create another account that has right for sudo but is not a root equivalent (hint, hint ;) )

---

### Post by gheywood on 2007-06-29
BTW, if I did want to enable the root account, what would be the command to do it (or which file would I edit)?

---

### Post by d_xtremw on 2007-06-29
I can't remember how exactly i did it but theres a thread somwhere in general help that shows u exactly how to do it.  from what i remember u type "sudo passwd root" and you enter your own password and then the password you want for the root account;

---

