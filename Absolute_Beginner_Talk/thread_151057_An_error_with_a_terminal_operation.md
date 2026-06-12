---
title: "An error with a terminal operation"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by Ob1 on 2006-03-27
> requested operation requires superuser privilege

well, i am the one and only user on this OS.

---

### Post by gnu2tux on 2006-03-27
you still need to become superuser:

if at the terminal:

$sudo [program you wish to run]
Password: <your password>

if running from a gui:

gksu [program you wish to run].

---

### Post by synchroswimr on 2006-03-27
[QUOTE=gnu2tux]you still need to become superuser:

if at the terminal:

$sudo [program you wish to run]
Password: <your password>

if running from a gui:

gksu [program you wish to run].[/QUOTE]

I am having problems with the same thing -- I try to run 'sudo apt-get install  gstreamer0.8-mad' like that, also with the $ in front, but it never prompts me to put in my password!

---

### Post by taurus on 2006-03-27
[QUOTE=synchroswimr]I am having problems with the same thing -- I try to run 'sudo apt-get install  gstreamer0.8-mad' like that, also with the $ in front, but it never prompts me to put in my password![/QUOTE]
the $ sign in front is a prompt and you are not supposed to type that in!!!  Are you saying that this command doesn't work at all?
```

sudo apt-get install gstreamer0.8-mad

```
It doesn't even prompt you for a password, then run this command at the prompt (from a terminal) and past the output there then...
```

id

```

---

### Post by synchroswimr on 2006-03-27
[QUOTE=taurus]the $ sign in front is a prompt and you are not supposed to type that in!!![/QUOTE] 
sorry, I guess I misunderstood.  

> 
Are you saying that this command doesn't work at all?
```

sudo apt-get install gstreamer0.8-mad

```
I am asked to put in my password, which I do, very carefully, and get this output:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

So I run the requested funtion, and it says I need to be a superuser.  If I attempt to run the gstreamer install again, and am not asked for password again.

> 
It doesn't even prompt you for a password, then run this command at the prompt (from a terminal) and past the output there then...
```

id

```
Here is the output:
uid=1000(stacy) gid=1000(stacy) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(lpadmin),105(scanner),106(admin),1000(stacy)


Thank you

---

### Post by gnu2tux on 2006-03-27
so do just that:

```

sudo dpkg --configure -a

```

it should fix it :)

---

### Post by synchroswimr on 2006-03-27
[QUOTE=gnu2tux]so do just that:

```

sudo dpkg --configure -a

```

it should fix it :)[/QUOTE]
Oh, I wasn't putting sudo in front of it.  What does "sudo" mean/stand for/do?

---

### Post by meborc on 2006-03-27
long story... but every ubuntian should read this! ;) 

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by IYY on 2006-03-27
Sudo stands for "superuser do", and it means "execute the following command as a superuser". Traditionally, administration tasks were done by logging in as a user called 'root'. Ubuntu takes the more modern approach by locking the root account, and allowing certain users to use "sudo".

---

