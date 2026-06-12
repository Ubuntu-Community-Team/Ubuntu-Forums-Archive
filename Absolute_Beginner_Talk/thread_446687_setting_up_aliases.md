---
title: "setting up aliases"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by ThePolemistis on 2007-05-17
Hi

I have downloaded leafpad and really like it, as its very similar to notepad in windows

the only problem is that in the terminal I want to call it notepad
so if i want to open a file i want to use the command
notepad filename
as oppose to
leafpad filename

Would an alias be the best way to do this? and how can i implement it?

---

### Post by taurus on 2007-05-17
Or you can create a symbolic link to it.  _Assuming_ you installed leafpad to /usr/bin, run

```
cd /usr/bin
sudo ln -s leafpad notepad
```

---

### Post by ThePolemistis on 2007-05-17
> **taurus said:**
> Or you can create a symbolic link to it.  _Assuming_ you installed leafpad to /usr/bin, run

```
cd /usr/bin
sudo ln -s leafpad notepad
```


nice thanks man... it works

just out of curiousity,,, is it possible to see all the symbolic links created??

---

### Post by earobinson on 2007-05-17
or you could add > alias test='echo test' to the .bashrc file in your home dir. (This lets you do more than just link commands eg I can make an alias for the command ```
ls -a | grep music
``` but no a symbolic link.

---

### Post by taurus on 2007-05-17
You have to be in the directory and do the listing to see them.

```
ls -la /usr/bin | more
```
Tab the space bar for the next 24 lines or the return key for next line.

---

### Post by earobinson on 2007-05-17
Sure,

you can do a ```
ls -l | grep "lrwxrwxrwx"
``` in the dir that you want to see all the links in. to see all your alias just type```
alias
```

---

### Post by earobinson on 2007-05-17
> **taurus said:**
> You have to be in the directory and do the listing to see them.

```
ls -la /usr/bin | more
```
Tab the space bar for the next 24 lines or the return key for next line.
That works 2

---

### Post by ThePolemistis on 2007-05-17
> **earobinson said:**
> Sure,

you can do a ```
ls -l | grep "lrwxrwxrwx"
``` in the dir that you want to see all the links in. to see all your alias just type```
alias
```

hmmm... i typed alias and all I get is:

```
alias ls='ls --color=auto'
```

I don't see the notepad one I creaed.. although the notepad does work

---

### Post by earobinson on 2007-05-17
> **ThePolemistis said:**
> hmmm... i typed alias and all I get is:

```
alias ls='ls --color=auto'
```

I don't see the notepad one I creaed.. although the notepad does work
did you add it to your .bashrc file? can you post it?

---

### Post by Cypher on 2007-05-17
> **ThePolemistis said:**
> hmmm... i typed alias and all I get is:

```
alias ls='ls --color=auto'
```

I don't see the notepad one I creaed.. although the notepad does work
You need to either "source ~/.bashrc" or log-out and log back in to load any new aliases..

---

### Post by ThePolemistis on 2007-05-17
> **earobinson said:**
> did you add it to your .bashrc file? can you post it?

Initially i didnt put it in my .bashrc file... but now I hav but still the alias keyword displaying notepad is not working. Although notepad command works perfectly (with or without adding to .bashrc). Does adding to bashrc mean it will remain even after reboot?

here is my .bashrc file,, I added it towards the bottom. The alias word does not show notepad in it,, just ls
alias ls='ls --color=auto'

.bashrc file:

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'
alias notepad ='leafpad'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```

---

### Post by ThePolemistis on 2007-05-17
> **Cypher said:**
> You need to either "source ~/.bashrc" or log-out and log back in to load any new aliases..

tried it... i get error:
> 

bash: alias: notepad: not found
bash: alias: =leafpad: not found


what exactly am I supposed to type in the .bashrc to make notepad = leafpad because i typed:
> 
notepad = 'leafpad'

---

### Post by Cypher on 2007-05-17
Remove all spaces around the command. Type the following into the terminal
```

alias notepad='leafpad'

```
then type 
```

alias

```
to see notepad listed, if that worked, add that to your .bashrc exactly the same way. Bash doesn't like the space around "="..

---

### Post by drs305 on 2007-05-17
I keep all my aliases in a separate file and they are always available on boot-up. If you don't want to reboot, you can close all your terminal windows and reopen them (there is a command to just refresh the aliases to do the same thing but I don't remember it).

To have a separate alias file, edit your .bashrc file and add the following (I start the filename with .bash so it's located alphabetically near the .bashrc file):

```

if [ -f ~/.bash_yourfilename ]; then
    . ~/.bash_yourfilename
fi

```

Then create a file named .bash_yourfilename in your home directory and insert an alias in the following format:

```

alias sai='sudo aptitude install '				

```

This example allows me to type 'sai' anytime I want to install a program via the terminal command 'sudo aptitude install'.

---

### Post by brennydoogles on 2007-05-17
I believe the reason you can't find you alias is that you didn't make one. Earlier you made a symbolic link from leafpad to notepad, effectively creating a new command (and technically a new program) for yourself.

> **ThePolemistis said:**
> nice thanks man... it works

just out of curiousity,,, is it possible to see all the symbolic links created??

---

