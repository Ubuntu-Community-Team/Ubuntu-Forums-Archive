---
title: "I don' t want sudo, I I want root - Where is the password?"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by emamm on 2006-04-01
Hello

I am new to Ubuntu. I have noticed that during installation, the process doesn' t ask for a root password, If suopd works,  I would be ok, but it doesn't .  Teh first thing I did was:
 show the updates (there is 350 updates) but a window pops out asking for a password. Which is the password to enter?  

I need to install some software but I don't have root permisson.

How to create an use a root user?   

Many thanks

Ed

---

### Post by cwaldbieser on 2006-04-01
[QUOTE=emamm]Hello

I am new to Ubuntu. I have noticed that during installation, the process doesn' t ask for a root password, If suopd works,  I would be ok, but it doesn't .  Teh first thing I did was:
 show the updates (there is 350 updates) but a window pops out asking for a password. Which is the password to enter?  

I need to install some software but I don't have root permisson.

How to create an use a root user?   

Many thanks

Ed[/QUOTE]

The first user account created is a sudo user.  Just use "sudo" and enter your normal password for that user.

Note that if you did an expert install, things are a little different, as you are expected to set up admin accounts yourself during that process.

---

### Post by mstlyevil on 2006-04-01
[QUOTE=emamm]Hello

I am new to Ubuntu. I have noticed that during installation, the process doesn' t ask for a root password, If suopd works,  I would be ok, but it doesn't .  Teh first thing I did was:
 show the updates (there is 350 updates) but a window pops out asking for a password. Which is the password to enter?  

I need to install some software but I don't have root permisson.

How to create an use a root user?   

Many thanks

Ed[/QUOTE]

Enter you user password you use to log in. The account you created was your sudoer account.

---

### Post by taurus on 2006-04-01
And if you say that sudo doesn't work for you (use the same password that you use to log into your system), then you can give root's password by (from a terminal)
```

sudo passwd root

```

---

### Post by NeghVar on 2006-04-01
That password it is asking for is your password, assuminmg you were the one who installed ubuntu

---

### Post by baza41 on 2006-04-01
To make a root password.

sudo passwd root.

It asks for your normal password. Type this in.

Then it will say,


enter new unix password, type in the password you want for root.

confirm it.

Bingo! root now works.

To switch from normal user to root type, su.


Hope that helps.

---

### Post by gord on 2006-04-01
[ this ](https://wiki.ubuntu.com/RootSudo)has all the information you should need about sudo and using sudo [

---

### Post by catlett on 2006-04-01
You will not know the root password in Ubuntu it is kept by the system and not given out or put in by you. Durind install the sytem creates one and stores it. Your password is the only password(unless you made more than one account). The user name and password you created during install are the only two pieces of info you need. When you start and there is the log in screen, type your username and password. Any time you need to be root you do it by typing sudo before the command. Open the terminal type sudo and then the command. You will be prompted for a password, use your username's password. It isn't a different password. The system has your username down as a "superuser". Therefore it recognises your ability to type sudo to get root priveleges and only needs your password to confirm. If you are reading directions or guides from other distros they might not have sudo or su commands. In those distros you have to log out. Type in root and the password for root. Do the command. Log out. Log in as user. In Ubuntu there is no need for that. Type sudo before the command and enter your username password when prompted for a password. You will then have root priveleges for that command. If sudo and your password at prompt doesn't work, follow the earlier posts directions to create a root password. But after it is created you won't be typing it in during commands. It is all done by sudo and your user password.

---

### Post by emamm on 2006-04-01
Hello

Many thanks.  I got a grip of what is hapenning.

Ed

---

