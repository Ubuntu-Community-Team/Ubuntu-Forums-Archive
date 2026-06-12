---
title: "I need to run a command on logout."
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by JoeTheZombie on 2007-10-24
As the subject states, I need to run a command on logout.  I have a virtualbox VM that I need to savestate like:```
VBoxManage controlvm WindowsXP savestate
```

But it is a real pain to do this everytime I logout.

---

### Post by Inxsible on 2007-10-24
you can create an alias for the logout command and have a bash script run. this script will of course have the command that you want to run followed by the log out command.

```
alias newcommand='yourcommand -arguments; yourOtherCommand'
```You should then add the alias to the .bashrc of the root user or add it system wide by putting it in /etc/bashrc file.


So for you it could be something like```
 alias VBoxLogout='VBoxManage controlvm WindowsXP savestate;logout'
``` You could use any name instead of VBoxLogout

---

### Post by rax_m on 2007-10-24
I found a reference here [http://dsl.org/cookbook/cookbook_5.html](http://dsl.org/cookbook/cookbook_5.html) 
that says you put the command in .bash_logout (not the period) to run commands when exiting a shell. 
However, I'm not sure if it works when using a GUI like Gnome.

---

