---
title: "Ubuntu 6.06 Files, commands, super user"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2006-08-15
Okay, I was trying to install an Xmms theme this time, and I did something wrong. It wouldn't let me just click and drag the file, because permission was denied. I take that to mean I need to be super user.

But, it won't let me. I type Su in the terminal, it asks for password, I put my login password in, and it doesn't work! Authentication failed.

So I tried to move it in terminal. Navigated to the folder, and typed

[sudo mv -filename- -destination-]

But I typoed, and it made a NEW destination and screwed with the file.

Now I can't figure out how to delete the file.


So, A) How do I get administartive power, and
B) How do I delete the file with the terminal?


Oy. THough, if I get admin, I won't need to delete with terminal. So...

Anyway. Thank you for putting up with me.

---

### Post by David Corrales on 2006-08-15
Root account is disabled by default in Ubuntu. You can type **sudo su** to get a regular root shell.
If you just want to delete the file type **sudo rm /path/to/file**

---

### Post by LadyDoor on 2006-08-18
Ok, first open up a terminal and set the root password:

```
$ sudo passwd root
```

Now you can su to root whenever you want, although sudo is better for performing individual tasks.

As to how to remove the file, enter this command:

```
$ rm /path/to/the/offending/file.extension
```

P.S.:  Another good solution would be to give yourself ownership of the file.

```
$ sudo chown yourusername:yourusername nameofthefile
```

Now you can do what you want with it without being root *or* using sudo. And maybe you should do that before installing it to XMMS. I don't know.

---

### Post by Izzy25 on 2006-08-18
how do you get the password for root because i am tryin to install my printer through the CUPS website and it asks for username and password the username is supposed to be root and i type in my password that i use to login into ubuntu but thats not it is there a root password?

---

### Post by taurus on 2006-08-18
> **Izzy25 said:**
> how do you get the password for root because i am tryin to install my printer through the CUPS website and it asks for username and password the username is supposed to be root and i type in my password that i use to login into ubuntu but thats not it is there a root password?
You have to create one with

```

sudo passwd root
(your own password first...)
(root password...
(root password again...)

```

---

### Post by Izzy25 on 2006-08-19
ok thanks got my password set but i still cant log in with CUPS to install my printer any one now how to login in? or any other way to instal my HP PSC 1410 printer?

---

