---
title: "root password??"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by fpsdf on 2006-03-15
During the installation, i wasn't asked for choosing a root password. Now i need to use linux as root and i don't know the password. what should i do? thank you very much.

---

### Post by katarot on 2006-03-15
sudo -s 
the password is your own password

---

### Post by aysiu on 2006-03-15
You don't *need* to use Linux as root. You think that's the only way, so you *want* to use it that way.

Read these two links to see how you don't have to use Linux as root:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

After you understand the benefits of *sudo*, you can then say you *prefer* logging in as root. The second link also has instructions for how to change Ubuntu back to a traditional root/user Linux model.

---

### Post by mlind on 2006-03-15
this was maybe the first (of many..) gotcha's with Ubuntu. Althought typing sudo
in front of every command you need to execute as a root user is  somewhat
frustrating, it has it's benefits. Just check the docs aysiu gave you.

---

### Post by hw-tph on 2006-03-15
[QUOTE=mlind]this was maybe the first (of many..) gotcha's with Ubuntu. Althought typing sudo
in front of every command you need to execute as a root user is  somewhat
frustrating, it has it's benefits. Just check the docs aysiu gave you.[/QUOTE]

You don't have to type sudo in front of every command. **sudo -i** gives you pretty much all root, including the correct $LOGNAME and other environment variables. Refer to sudo(8) for more help.

```
hakan@devon:~$ sudo echo $LOGNAME
hakan
hakan@devon:~$ sudo -i
root@devon:~# echo $LOGNAME
root
```

Håkan

---

### Post by mlind on 2006-03-15
[QUOTE=hw-tph]You don't have to type sudo in front of every command. **sudo -i** gives you pretty much all root, including the correct $LOGNAME and other environment variables. Refer to sudo(8) for more help.

```
hakan@devon:~$ sudo echo $LOGNAME
hakan
hakan@devon:~$ sudo -i
root@devon:~# echo $LOGNAME
root
```

Håkan[/QUOTE]

yeah, the thing is that I want to avoit root terminals like cancer and only do
any root access related by using sudo. I've broken my system twice when doing
 *sudo su* followed by *rm -rf* or similar oops.

After that I decided to always use sudo so I need to think before doing the damage :oops:
and it leaves my trails on /var/log/auth.log

---

### Post by last_one on 2006-04-22
I had the exact same question when I started using ubuntu.  I tried the su command but it never worked.

---

