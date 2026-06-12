---
title: "[SOLVED] Auto start of a sudo process"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by ene_dene on 2008-03-01
I need to autostart process noip2. The problem is that I need to be superuser, so I can't go to system->preferences->sessions and then write sudo noip2 because I don't know how to run a sudo command and input password in one line (I need to press enter to be asked a question). The script would probably be the best solution, but I don't know how to do it, If someone could write it for me -> script that does the following:
sudo noip2
enter a password.

---

### Post by tdrusk on 2008-03-01
```
gksudo noip2
```

that should prompt you for a password.

---

### Post by y-lee on 2008-03-01
the man page for sudo says that using the -S option reads the password from stdin, so ```
echo "password" | sudo -S whatever
``` should work.

In my case my password contains special characters used by bash so i had to use

```
echo 'password' | sudo -S whatever
```


However, it's not a good idea to leave passwords in plain text where others can possibly see them.

Another way is to [edit the sudoers file]("http://php.8ez.com/drsmall/blog/?p=157") to allow your command to run without a password. Again maybe not the best idea.:(

But those are the only two options I know of. If there is a better option I would love to learn it :)

---

### Post by Cypher on 2008-03-01
> **y-lee said:**
> the man page for sudo says that using the -S option reads the password from stdin, so ```
echo "password" | sudo -S whatever
``` should work.

In my case my password contains special characters used by bash so i had to use

```
echo 'password' | sudo -S whatever
```


However, it's not a good idea to leave passwords in plain text where others can possibly see them.

Another way is to [edit the sudoers file]("http://php.8ez.com/drsmall/blog/?p=157") to allow your command to run without a password. Again maybe not the best idea.:(

But those are the only two options I know of. If there is a better option I would love to learn it :)

Working with the idea of modifying the /etc/sudoers file, you can modify it such that ONLY the noip2 program can be executed without requiring your password. All other superuser commands will continue to require your password..

---

### Post by y-lee on 2008-03-01
> Working with the idea of modifying the /etc/sudoers file, you can modify it such that ONLY the noip2 program can be executed without requiring your password.

Indeed that is what i meant by "*edit the sudoers file to allow **your command** to run without a password*."

**Just allow that one command to run without a password!**

---

### Post by glennric on 2008-03-01
Is noip2 a graphical application or is it a command line app or script?  If it is just command line you could use cron.  It is possible to use graphical apps from cron as well, but is more difficult.

---

### Post by forrestcupp on 2008-03-01
I once had a process that required sudo in my startup sessions, and I don't think it asked for a password.  Just make a script in your text editor like this:
```
#!/bin/bash
sudo noip2
```
And save it to a place and under a name you will remember.  Then type:
```
cd /path/to/file
chmod +x ./filename
```
To make it executable.  Substituting /path/to/file for wherever you put it, and ./filename with whatever you named it.

Then put that script in your sessions, and you should be ready to go.  If it needs a password, it will prompt you when you start up.  But like I said, I think I did it before and didn't even need to enter a password.

---

### Post by y-lee on 2008-03-01
Also see [ Run noip at startup]("http://ubuntuforums.org/showthread.php?t=15743") here on the forums which i just found.

One or more of these suggestions surely has got to work :lolflag:

---

### Post by ene_dene on 2008-03-01
Thank you guys, It worked!

---

### Post by y-lee on 2008-03-01
> Thank you guys, It worked!

Glad to hear :popcorn:

Share what you did and please mark this thread as solved. makes the forums easier to use :)

---

### Post by ene_dene on 2008-03-01
I used gksudo noip2, although echo worked too, but I'm not happy about password being visible.

I'm sorry about "solved" I haven't seen that option, so I'll click on it now for all my solved threads.

---

