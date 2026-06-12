---
title: "Need quick SSH help. (Needs to be done today)"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by RussianVodka on 2006-09-27
All my Computer Science labs have to be handed in through SSH. I came late to class, so I didn't have to time to actualy send the lab, though I did do it. But I figured that Linux comes standard with SSH, so I'll be able to hand it in without trouble (it needs to be in by midnight today).

The first lab is basicaly nothing more than an introduction on handing in labs in SSH.

Here is it's web page:

[http://www.cs.sunysb.edu/~cse110/labs/lab0.html](http://www.cs.sunysb.edu/~cse110/labs/lab0.html)

After you log in, you type "bash" and get into a regular bash terminal, which I know how to use well.

The problem is that I don't know how to log in.

I know my user name and password, and I know all the other information (I think it's listed on the web page). But I don't actualy know how to use SSH.

When I use it on the labs computer, I basicaly double click on an icon and I get this box:
[img]http://www.cs.sunysb.edu/~cse110/labs/ssh_login_screen.jpg[/img]

And then it's smooth sailing from there.

But when I try to start up ssh in my linux terminal, I get this:
```

egor@egor-laptop:~$ ssh
usage: ssh [-1246AaCfgkMNnqsTtVvXxY] [-b bind_address] [-c cipher_spec]
           [-D port] [-e escape_char] [-F configfile]
           [-i identity_file] [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [user@]hostname [command]
egor@egor-laptop:~$

```

I'm completely clueless. Can anyone help?

---

### Post by RichJacot on 2006-09-27
From your laptop you'll need to ssh to the other host.

ssh hostname

In place of hostname you may need to FQN, i.e. ssh hostname.domain.com

Does this help?

---

### Post by jimbren on 2006-09-27
Post your assignment along with your username and pasword and someone will do it for you.

---

### Post by jimbren on 2006-09-27
Just kidding.

Easy as pie.  

You would do something like this: 
```
ssh loginname@sparky.ic.sunysb.edu
```

You'll be prompted for your password, and then you're off.

If your username is the same on your machine as it is as school, then you could just do this:
```
ssh sparky.ic.sunysb.edu
```

---

### Post by mitch.c on 2006-09-27
> **RussianVodka said:**
> The problem is that I don't know how to log in.

But when I try to start up ssh in my linux terminal, I get this:
```

egor@egor-laptop:~$ ssh
usage: ssh [-1246AaCfgkMNnqsTtVvXxY] [-b bind_address] [-c cipher_spec]
           [-D port] [-e escape_char] [-F configfile]
           [-i identity_file] [-L [bind_address:]port:host:hostport]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-R [bind_address:]port:host:hostport] [-S ctl_path]
           [user@]hostname [command]
egor@egor-laptop:~$

```

I'm completely clueless. Can anyone help?
Gotta tell ssh who you're trying to connect to! 8) 
```
ssh sparky.ic.sunysb.edu
```

---

### Post by RussianVodka on 2006-09-27
Never mind, I asked my dad and the command was ```
ssh -Y -l [rest of information]
```

---

