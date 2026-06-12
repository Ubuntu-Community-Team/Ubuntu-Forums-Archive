---
title: "alias question"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by sublimeprogie on 2006-07-18
hi, i posted this in an alias thread, but it didnt get answered, so i thought i would throw it in a more appropriate place.  

do you have to do anything to get your aliases activated, i read to put my aliases in my .bash_profile. but i have restarted my computer and everything and they dont seem to work. 

this is what i have right now

```

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

alias today='date +"%A, %B %-d, %Y"'

alias l='ls -l' 
```

thanks

---

### Post by professor_chaos on 2006-07-18
try putting the aliases in .bashrc

---

