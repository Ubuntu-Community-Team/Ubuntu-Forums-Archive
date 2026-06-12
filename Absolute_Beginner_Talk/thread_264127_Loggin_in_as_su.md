---
title: "Loggin in as su?"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by mercat on 2006-09-24
All: I'm trying to install java runtime environment and, according to the instructions, to install system-wide, I need to log in as "su" (super user, i assume?). How do I do this? Tried using the password I use to access Ubuntu on start-up, but that doesn't work. I installed Ubuntu and am the only one using it, so I thought I'd have super user privileges. Thanks.

Carl

---

### Post by Sef on 2006-09-24
Easy way to install Java.

1) Add universe and multiverse to your repositories. To add the them, [click here.]("https://help.ubuntu.com/community/Repositories/Ubuntu")

2) Next Applications > Add/Remove > enable unsupported applications and then commercial applications > then write java in the search box (upper right) > go down to Sun Java 5.0 Runtime > Check it > click on apply > follow instructions to install it.

---

### Post by dbd on 2006-09-24
You don't need to log in as run to install java, just see here:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

For future reference, if you want to run a program as root. Then on the command line just type "sudo " before the command.

---

### Post by hearnden on 2006-09-24
The superuser account is called 'root', and has all the super user privileges.  The first account you set up in Ubuntu does not have superuser privileges, however it has the privelege of being able to ask the superuser account to execute commands, using 'sudo' (Super-User DO).

So you can either install by issuing sudo commands in a terminal, or you can temporarily become root using 'su' (or you can do 'sudo su' to ask the super-user account to let you switch to the super-user account).

I don't think that GDM will let you have a graphical session as root, you have to start all super-user stuff through the terminal.

However the (Sun) JRE and SDK should be in the repositories, so:

```

$ sudo apt-get install sun-java5-jre

```

should install everything and *just work*.

(see in the Ubuntu guide:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)
[http://ubuntuguide.org/wiki/Dapper#How_to_install_JRE_v5.0_Update_8](http://ubuntuguide.org/wiki/Dapper#How_to_install_JRE_v5.0_Update_8)
)

---

### Post by Sef on 2006-09-24
Here is why you shouldn't log in or use root:  [Root/Sudo]("https://help.ubuntu.com/community/RootSudo")

As for installing: [Installing on Ubuntu.]("http://www.psychocats.net/ubuntu/installingsoftware.php")

---

### Post by mercat on 2006-09-24
Thanks, all, for the answers. Really appreciate the speedy replies!

Carl

---

### Post by Dinerty on 2006-09-24
> **mercat said:**
> All: I'm trying to install java runtime environment and, according to the instructions, to install system-wide, I need to log in as "su" (super user, i assume?). How do I do this? Tried using the password I use to access Ubuntu on start-up, but that doesn't work. I installed Ubuntu and am the only one using it, so I thought I'd have super user privileges. Thanks.

Carl

Basically all it means is type:

```
sudo
```

before your commands, basically if you where trying to install something from source, it may look like this:

```
 make install 
```

however if they guide said log in as superuser, it would mean this

```
sudo make install
```

---

