---
title: "[SOLVED] Permanent aliases"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by OlyPerson on 2008-03-30
So in my attempt to learn about the command line, I've started looking into aliases to make things simpler.  I know the basic structure of them, but I cannot seem to make them permanent, because when I exit out of the shell they are forgotten.
I know I am supposed to go into bash_profile or bashrc or something like that, but I cannot get into any of them :confused:
I have tried opening them with vi, edit, gedit, searched for them, etc but I can't seem to find the file where I am supposed to save the aliases that I want, it's kind of annoying me to tell you the truth.
Thanks if anyone can help me find where to put the new aliases!

Oh, and I'm using Gutsy.

---

### Post by c-ron on 2008-03-30
Try .profile 

Check out Getting Started with BASH - A Bash Tutorial:
[http://www.hypexr.org/bash_tutorial.php](http://www.hypexr.org/bash_tutorial.php)

---

### Post by OlyPerson on 2008-03-30
I've tried that too :(

Am I even doing this right?  I'm opening the file with vi by just writing "vi .profile"
Is that the right way to go about it?  Because when I do that it says that I am opening up a new file, and I don't think that I want that.

---

### Post by c-ron on 2008-03-30
I don't recommend vi if you're not familiar with it.
Use nano instead.

```
nano ~/.profile
```

---

### Post by OlyPerson on 2008-03-30
I dunno, I kinda have gotten used to vi, doesn't seem all that complex or anything.  So at the end of that, what do I write?  Right now all I see is ```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f ~/.bashrc ]; then
        . ~/.bashrc
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

```
at the end of that do I write, eg, alias cd='cd && ls -l'?

---

### Post by taavikko on 2008-03-30
edit ~/.bashrc file, remove the comments from the next lines
> #if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi


And then create corresponding file ~/.bash_aliases
and add aliases you want...
alias update='sudo apt-get update'
for an example
save and quit, and update bash simply by typing
```
bash
```

---

### Post by OlyPerson on 2008-03-30
Awesome!  Thanks, for some reason I was just not able to get into bashrc and I didn't realise that I had to make the bash_aliases file myself, but now it all works.

---

