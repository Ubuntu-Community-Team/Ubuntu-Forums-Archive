---
title: "Firestarter ERROR but Firestarter Works OK"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-04-05
I get this error message when I bootup, however Firestarter seems to work OK.
How do I stop this message or delete it ?

```

[B]Insufficent privileges
You must have root user privileges to use Firestarter[/B]
```

I tried Arnieboys suggestion at the bottom of my Post (other post with similar problems)  but it hungup my system.
after awhile I was able to proceed.

I guess I need to know why it is going on and then maybe we can fix it.
Thanks for any help.

Remember I don't have to do anything firestarter automatically starts by itself Ok I just get this message.

---

### Post by mlind on 2006-04-05
Could be configuration related, have you tried reinstalling firestarter?
You probably know that running firestarter need root privileges.

---

### Post by kent41 on 2006-04-05
Before I re-install Firestarter I would like to know why I get the error message so it could someone else.
Thanks

---

### Post by mlind on 2006-04-05
do you mean you get the error when firestarter service is trying to start
or when your trying to start firestarter GUI ?

I repeat, you _must_ run firestarter with root privileges or you get an error like that.
use run firestarter GUI using command *sudo firestarter* or *gksu firestarter*

if it's on bootup, does it happen on entering certain runlevel?
does *dmesg* report that error aswell?
does root own /etc/init.d/firestarter file and have +rwx permissions for it?

if you execute *sudo /etc/init.d/firestart restart* do you get that error?

---

### Post by x5452 on 2006-04-05
sorry to jump in on your thread here but I have two questions, first what even is firestarter?  and how come every time I boot up i get a mesage saying enter password to work /usr/sbin/firestarter ??
i dont even know what it is, any ideas?   

sorry again for replying here its not my own thread question

---

### Post by kent41 on 2006-04-05
When I say bootup I mean the end of bootup and after i have entered Username and password and the last screen comes up.   (gnome?)

No I don't see the error in dmesg.

The permissions and owner are
```

-rwxr-xr-x  1 root root 1472 2005-05-28 20:10 firestarter

```

when I run **/etc/init.d/firestarter restart **firestarter does not run or start and I get no errors. I just get the following:

```
kent@ubuntu1:~$ sudo /etc/init.d/firestarter restart
Stopping the Firestarter firewall:done.
Starting the Firestarter firewall: done.
kent@ubuntu1:~$
```

---

### Post by mlind on 2006-04-06
yes, but you didn't try running just

```

sudo firestarter

```

which means run firestarter on root privileges. Firestarter consists of service and
binary (actual GUI). Service is automatically loaded started on runlevels 1-5, which
means that /etc/init.d/firestarter script is executed automatically and you don't
need to worry about that.

What you just need to do is to launch the GUI.

@x5452
firestarter is a GUI frontend for IPTABLES, which is packet filtering firewall built-in linux kernel. With firestarter it's easy to configure IPTABLES, like opening ports for services. firestarter is simple (which makes it somewhat limited too).

---

### Post by x5452 on 2006-04-06
is there a way to turn off it asking for my password everytime i boot up?

---

