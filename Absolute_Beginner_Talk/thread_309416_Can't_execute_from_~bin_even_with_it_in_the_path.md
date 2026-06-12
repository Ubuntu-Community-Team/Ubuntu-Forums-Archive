---
title: "Can't execute from ~/bin even with it in the path"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Nerbit on 2006-11-29
I have been having some trouble with a small but annoying problem that I was hoping someone might know a quick answer to.  I can not seem to execute files in my ~/bin directory without specifying the full path to them.

I created a file called ~/bin/test with the following inside it:

#! /bin/bash
echo Hello World!

made it executable... chmod +x test

Within my .bash_profile it is adding that directory to my path.  
If I type echo $PATH, I get /home/me/bin:/usr/local/sbin:...
If I type which test it shows /home/me/bin/test
If I type ~/bin/test I get Hello World!

If I type test I get nothing

/home is mounted using defaults (although, obviously /home is rw since I can execute it with ~/bin/test).

This happens from a local login (this is a server install so only command prompt) or from ssh remote login.

Any help would be appreciated, I know this is a small problem, but it has me stumped :)

---

### Post by taurus on 2006-11-29
Add these two lines to your ~/.bashrc.

```
PATH=$PATH:/home/me/bin
export PATH
```
Then run

```
source ~/.bashrc
test
```

---

### Post by Nerbit on 2006-11-29
> **taurus said:**
> Add these two lines to your ~/.bashrc.

Unfortunately, that didn't work for me :(.

As I said above, the directory is already in my path, and which test shows it.  I can't imagine why it isn't executing.

Below is the screenshot (other than changing my login name to "me") after trying your suggestion (after editing the .bashrc and running source ~/.bashrc).

```

[me@hermes:~]$ echo $PATH
/home/me/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/home/me/bin
[me@hermes:~]$ which test
/home/me/bin/test
[me@hermes:~]$ ~/bin/test
Hello World!
[me@hermes:~]$ test
[me@hermes:~]$

```

---

### Post by schilcha on 2006-11-29
Hi!

If you use bash and execute the command "test", bash will use its builtin command with the name "test" -- bash's man-page will tell you what exactly it does. If you want to execute your script with the same name, you have to supply the path to the executable. Try renaming your script to a yet unused named to avoid further conflicts. 

Best,
   schicha

---

### Post by Nerbit on 2006-11-29
> **schilcha said:**
> Hi!

If you use bash and execute the command "test", bash will use its builtin command with the name "test" -- bash's man-page will tell you what exactly it does. If you want to execute your script with the same name, you have to supply the path to the executable. Try renaming your script to a yet unused named to avoid further conflicts. 

Best,
   schicha

Argh, that explains it :).  I changed the name from test to hello and it works perfectly.  Thanks for the help both of you.  I know it was a small problem, but the strangeness of it was really driving me nuts.

---

