---
title: "authentication??"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Hawk__0 on 2007-04-25
ok well, the first time i issued the sudo command it asked me for my pass, so ok i did that no problem.  then i try installing a program and i get an error about how the directory doesnt belong to me.  this is my one and only account.  i type "su -"(log into root, correct?) then my password wont work...
here is the output:

```

steve@steve-desktop:~$ sudo sh  ./install-crossover-standard-demo-6.0.1.sh
Verifying archive integrity...OK
Uncompressing CrossOver Linux Standard
....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
The '/home/steve' directory does not belong to you.
Point $HOME to your home directory and try again.
steve@steve-desktop:~$ su -
Password: 
su: Authentication failure
Sorry.
steve@steve-desktop:~$ 



```



update**************************

ok so i log on as root :P
now i have this problem:


```

root@steve-desktop:/home/steve# sudo sh  ./install-crossover-standard-demo-6.0.1.sh
Verifying archive integrity...OK
Uncompressing CrossOver Linux Standard
....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

The DISPLAY variable is not set.  You should either login to as root or use
the command "su" with no flags, to make sure setup has an X display to use.

The setup program seems to have failed on x86/glibc-2.5
Check the system requirements at:
http://www.codeweavers.com/products/cxoffice/requirements/
root@steve-desktop:/home/steve# 

```

---

### Post by 007Bond on 2007-04-25
Well for starters the su password is your root password which is not set by default.

---

### Post by Drewski on 2007-04-25
Isn't the root account disabled in Ubuntu by default?
From what I've seen you should be using sudo instead of su.

---

### Post by STREETURCHINE on 2007-04-25
type

        ```
sudo su
```

into terminal  then your password and that should solve that problem
to go to root acc  from your normal acc " sudo su "is required

but remember logging in to your root acc is very dangerous and not recomended,so if you do this be very carefull

---

### Post by Hawk__0 on 2007-04-25
steve@steve-desktop:~$ sudo su sh ./install-crossover-standard-demo-6.0.1.sh
Password:
Unknown id: sh
steve@steve-desktop:~$ sudo su ./install-crossover-standard-demo-6.0.1.sh
Unknown id: ./install-crossover-standard-demo-6.0.1.sh

---

### Post by bobplano on 2007-04-25
you don't need sudo su because that is redundant if you use it for every command. sudo su should log you in as root so you shouldnt have to use sudo for each command. i recommend using sudo though because being root and entering commands without knowing what they do is dangerous

---

### Post by Hawk__0 on 2007-04-26
ok well that asside it still gives me an error

---

