---
title: "how do I remove the ~ in the shell prompt?"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by bradmayne on 2007-07-19
how do I remove the ~ character in the shell prompt?

This is how my prompt looks now:

brad@brad-laptop:~$

---

### Post by felicity on 2007-07-19
Are you sure you want to? That is telling you what directory your in, your home directory. Try changing directories and you will see it change. You 'can' remove that feature entirely, but then you wouldn't know where you were easily.

---

### Post by bradmayne on 2007-07-19
No it's still there when I change directories.  I didn't have the ~ character until I was told to put it there when I was installing a package awhile back.  Now, I can't get rid of it.  I tried changing directories to the Desktop.  The ~ was still there.  So if you can tell me how to get back to my original bash prompt that would be great.

---

### Post by Nythain on 2007-07-19
what you see at yoru bash prompt is assigned within your .bashrc file in your home directory... be carefull what you edit in there... you could type
```

cat ~/.bashrc

```
and post the output and one of use could try to find it for you, so you dont go around making random changes in an unfamiliar file

---

### Post by bradmayne on 2007-07-19
ok here's the output:

brad@brad-laptop:~$ cat ~/.bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

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

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
brad@brad-laptop:~$

---

### Post by meierfra on 2007-07-19
~ is just a short cut for  /home/username. If you change to a folder outside the home directory 
 (for example  cd  /etc)  you won't have the ~.

---

### Post by bradmayne on 2007-07-20
okay i tried that with the cd /etc

your right the ~ does disappear when I change directories. Why was the ~ character not there with the default installation?

---

### Post by meierfra on 2007-07-20
It always has been there for me. So I'm pretty sure that  the ~ is the default setting.

---

### Post by grishenko2000 on 2007-07-20
[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html")

Provides a good tutorial of how to change the bash prompt

---

### Post by bradmayne on 2007-07-21
I don't remember seeing the ~ until 3 weeks ago or so.  I was trying to configure some utility and in the README  it said to do something with the ~ character.  I think the utility was for pwm and lmsensors.  I don't really remember though at this point.  My girlfriend wants to install ubuntu on Sunday so I'm going to remember to take a look at the default bash.

---

### Post by eentonig on 2007-07-21
> PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$

If you ever want to continue with changing the bash prompt. This is the line you need to adapt.


And to show you what the normal behavior is . Don't mind the first part. That's how my shells open up.
> Hello rfonteyn today is Sat Jul 21 09:05:28 CEST 2007

     July 2007      
Su Mo Tu We Th Fr Sa
 1  2  3  4  5  6  7
 8  9 10 11 12 13 14
15 16 17 18 19 20 21
22 23 24 25 26 27 28
29 30 31            
                    


Uptime for gauloises is 3 days,
The news trivia of the day are...
07/21   First Train Robbery, Jesse James gets $3000 near Adair, Iowa, 1873
07/21   Vietnam divided at 17th parallel, 1954
07/21   National Holiday in Belgium
rfonteyn@gauloises:~$ cd /etc
rfonteyn@gauloises:/etc$ cd 
rfonteyn@gauloises:~$ cd /var/log/
rfonteyn@gauloises:/var/log$ cd ~/Music
rfonteyn@gauloises:~/Music$ 

So you can see that the '~' comes and goes depending on where you are. And that you can use it yourself to navigate.

---

