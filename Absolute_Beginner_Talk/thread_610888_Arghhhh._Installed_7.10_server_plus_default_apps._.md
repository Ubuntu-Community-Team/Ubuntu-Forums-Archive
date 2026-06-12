---
title: "Arghhhh. Installed 7.10 server plus default apps. Can't sudo?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by asteel on 2007-11-12
Hi everyone

Total newbie so expect this to be easy Q. Have searched loads but can't find an answer.

I have installed ubuntu server 7.10. from cd created user called administrator gave it apssword

then selected all software in the installer mysql, apache2 etc......

when asked for root password for mysql entered same pass as administrator...


Now when boot and want to change from dhcp to static IP i can't run sudo passwd root....

Any ideas???

---

### Post by Hospadar on 2007-11-12
what heppens when you sudo?  are you still in the "admin" group?

---

### Post by asteel on 2007-11-12
when I try to run any sudo commands it responds with administrator is in in sudoers. this will be reported.or words to the same efect.....

when Ijust installed base system I could do the sudo password root command.

but when I installed the additional apps something must have happened to stop this

I have installed 3 times and the same happened each time plus one without additional apps which allowed sudo


administrator is the user by the way

---

### Post by mysticrider92 on 2007-11-12
It almost sounds like you did not create a regular user in the install, but I don't know how that is possible. Try running whatever command you need without sudo and see what it does.

If it works, you will need to add a user with the useradd program. This user can have sudo privliges.

---

### Post by asteel on 2007-11-12
I am trying to change from dhcp to static ip so am running 
vi /etc/network/interfaces

it opens the file but only as read only.?!?!?

have tried just typing su
it asks for password but i don'tknow what it is....

---

### Post by spydon on 2007-11-12
My root password stopped work in Gutsy too...
Someone said that it was to complicated and that something maybe went wrong because i had special characters outside the first 8 characters...
It worked perfectly well in feisty and I don't see the point with restricting the password length and complexity. :confused:
Or did I misunderstand the question and your password is still working but it just doesn't work to sudo?

---

### Post by mysticrider92 on 2007-11-12
Did you call the account you created during the install administrator? It should have had whatever name you wanted for your login.

You will have to type a password to login, that is what it is asking for when you type su. 

And the fact that it opens the file read only means that you are using a normal account, so sudo should work.

---

### Post by asteel on 2007-11-12
login as: administrator
administrator@192.168.0.11's password:
Linux dz1 2.6.22-14-server #1 SMP Sun Oct 14 23:34:23 GMT 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Mon Nov 12 17:39:14 2007 from 192.168.0.2
administrator@dz1:~$ adduser
adduser: Only root may add a user or group to the system.
administrator@dz1:~$

---

### Post by zvacet on 2007-11-12
Boot in recovery mode and type 

```
adduser username admin
```

---

### Post by asteel on 2007-11-12
how do I do that?

AND 

canI do that in putty or do I need to hook a keyboard and monitor backup?

---

### Post by zvacet on 2007-11-13
When you start your comp you see grub menu with kernels and they recovery modes.Pick kernel with higher number and one line below is recovery mode.Select that to boot in to.You will see just terminal.Type comand from previous post in terminal where username is your username.By typing **admin** you will add user to admin group wich means you will be able to use sudo.You will have administrator privileges.

---

### Post by asteel on 2007-11-13
hi thanks for that.... I have followed the instructions...

got root@dz1: entered adduser administrator admin

got message the group 'admin' does not exist.

what now?!!?

this is so frustrating! I am so wanting to get myself a little linux server set up. There must be so many other people having this problem as I have just run the cd.. nothing clever and this what you end up having to do...

Thank you all by the way for your help....

---

### Post by asteel on 2007-11-13
Hi everyone.. I got sooooo mad with this issue that I have re-installed the system...

This time however I didn't install the mail server and postgre. All works perfectly..

Could these programs have been playing with the users and groups priviliges?

---

### Post by zvacet on 2007-11-13
Also in recovery mode 

```
addgroup admin
```

after that 

```
adduser username admin
```

---

### Post by az on 2007-11-13
> **asteel said:**
> 

when asked for root password for mysql entered same pass as administrator...



The "mysql root user" is not the same as a system user named "root".  If you create a user named "julie" on your system, mysql will not know or care about it.  If you create a user named "betty" in mysql, you will not be able to log into your system as "betty".  Mysql has users to access the databases, but it has nothing to do with the system.  The Mysql user named root is simply a mysql user and has nothing to do with the root acount on your Ubuntu OS.

By default in Ubuntu, the root login is dissabled.


> **asteel said:**
> 
administrator@dz1:~$ adduser
adduser: Only root may add a user or group to the system.
administrator@dz1:~$

That should be 

sudo adduser

You can not run things with elevated privileges without using sudo.

---

