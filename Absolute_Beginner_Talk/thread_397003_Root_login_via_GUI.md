---
title: "Root login via GUI"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by ameysalvi81 on 2007-03-30
hi all,
i am very new to linux, can some one help me how i can login as a root via GUI .........
as i want to login as root when ubuntu starts as prompt me for login......i tried there to login as root but it pop up the message as root administrator is not allowed to login from this screen.....but actually i want to login to GUI mode ubuntu as root user..........

---

### Post by STREETURCHINE on 2007-03-30
have a read of this 

  [http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

login as root is not really a good idea unless you have a specific reason to.

you can do sudo in terminal to get to root or open nautilus with root permissions to make changes,

how to open nautilus with root permissions 

                        ```
gksudo nautilus
```

then you can drag files to open as root.

if you choose to login as root all the time be carefull,the only option may be a complete reinstall

---

### Post by bunnny on 2007-03-30
As STREETURCHINE said, not the best thing to do, and I can't really see why you want to do it.

But if you want to do it anyway, this is how (it worked for my anyway)

1. Open gdmsetup as root in a terminal

```
sudo gdmsetup
```

Go to Security and choose "Allow local system administrator login"
Then close.

Now try to login as root (you maybe have to restart gdm: ctrl-alt-backspace)

If it don't work (msg. wrong password)

2. Set root password. Open a terminal and run:

```
sudo passwd root
```

and enter a new password.

That should work.

---

### Post by PurplePenguin on 2007-03-30
I'd like to join the chorus of people trying to talk you out of this.  Ubuntu (and linux in general) is secure because users do not have permanent root access.  Entering your password and adding sudo before a few commands here and there isn't too much of a hassle! :)

---

### Post by ameysalvi81 on 2007-03-30
Thanks to all for the quick reply .....
i know that it is not safe to do that but as i am very new to the linux so i dont know many linux commands so setup the thing i was to do as accessing the Files,Listening Music, Watching movies etc and setting many things ......

---

### Post by STREETURCHINE on 2007-03-30
just search the forums there are plenty of how to's ,

  [http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

ther is a usefull link and if you cant find a solution ask a specific question and some one will help,
they always do

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

there is anouther good site to read,

also google is your best friend,any problem you have has already been solved.

good luck.

---

### Post by eentonig on 2007-03-30
Especially if you're new to linux and don' know your way around very well... I would keep far away from hacks that allow you to login as a permanent root.

For starters, it doesn't help you as you just keeps you in a 'MS state of mind'. Forget what you've learned from Windows administration and learn your way up in the linux way of doing (and thinking) stuff.

More immenent, the danger of typing a desastrous command will bu much higher.

---

### Post by deuchar1 on 2007-03-30
The sudo environment takes a bit of getting used to when migrating from Windows but it's a better setup. Perservere and you'll gradually notice the advantages of it. It definitely seems like a bit of a bind at first, granted. 

gksudo nautilus is what I use - grants one-time only superuser access at STREETURCHINE said, and in a GUI filesystem environment.

---

### Post by elints on 2007-05-19
In kdm, root login is disabled.

Open /etc/kde3/kdm/kdmrc with kwrite or your fav editor. Find the root login line and change false to true and save. Then in user manager, select root and enable what privileges you need. 

It worked for me.

---

### Post by Najand on 2007-05-19
With your own responsibility, check [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) for your results.

---

