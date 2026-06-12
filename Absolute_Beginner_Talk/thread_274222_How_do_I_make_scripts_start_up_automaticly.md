---
title: "How do I make scripts start up automaticly?"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-10-09
Ok I've made some scripts. They work perfectly find when I add their destination each time I start up the console. But when I restart the console it just doesent work anymore. 

Example:

Lets say I have a script called myscript in the home/myname/bin folder. When I start up the console I will type this: export PATH=$PATH:/home/myname/bin and then each time I type myscript the script will start. According to this guide: [http://linuxcommand.org/wss0010.php](http://linuxcommand.org/wss0010.php) if I want my script to work each time I start the console I have to add export PATH=$PATH:/home/myname/bin i have to add it to my .bash_profile document. I have done this so my docuement looks like this:

# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
export PATH=$PATH:/home/myname/bin

But it still wont start up automaticly. What am I doing wrong? It really sux, because I have a really hard time continuing the guide, when I cant get this right.

Hope you get what I am saying otherwise tell me. It might be hard to understand..

Thanks in advance.

---

### Post by zappa on 2006-10-09
Don't put export in the file ;)
Should do it I think.

---

### Post by jincast90 on 2006-10-09
> **zappa said:**
> Don't put export in the file ;)
Should do it I think.

I tried just adding PATH=$PATH:/home/myname/bin still nothing. Did not help.

---

### Post by Sentinel83 on 2006-10-09
I am not sure how you make the script start automatically with code, but if you want to set the scripts to run at startup, just go to -

System --> Administration --> Sessions (if not under admin, its under prefs, cant remember)

Under the sessions window, choose startup, and put the path to the script you want to run.  When you login, the script will run.  Hope that helps some...

---

### Post by jincast90 on 2006-10-09
> **Sentinel83 said:**
> I am not sure how you make the script start automatically with code, but if you want to set the scripts to run at startup, just go to -

System --> Administration --> Sessions (if not under admin, its under prefs, cant remember)

Under the sessions window, choose startup, and put the path to the script you want to run.  When you login, the script will run.  Hope that helps some...

Tried it. It doesent work. Damn

---

### Post by tucoz on 2006-10-09
> # set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
PATH=~/bin:"${PATH}"
fi
export PATH=$PATH:/home/myname/bin

Isn't those lines redundant?
Anyway. try to remove the export line from .bash_profile and add the following to ~/.bashrc instead:

```
export PATH=$PATH:/home/myname/bin
```
If you want to run the script automatically each time you open up a terminal, try to add the scripts name to the bottom of ~/.bashrc.

---

