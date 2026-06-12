---
title: "'ls' displaying one file/folder per line"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2007-08-28
I just noticed that 'ls' has started displaying one file/folder per line like this:
```

james@Ubuntu:~$ ls ~
Books
Code
Desktop
Games
Images
moo.cpp
Music
Operating Systems
Web Sites
Work

```

where as before, it would always display it like this (taken from 'ls' output on my web server)
```

[stingray]$ ls
Maildir  jamesbowden.com  justpoetryinmotion.com  logs

```

I'm sure I havn't change anything. I can't think what has happened.

here is my .bashrc file if it helps.
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
# PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

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

```

Thanks
James

---

### Post by Mornedhel on 2007-08-28
This happens if you have a filename too long to fit in one half line. Otherwise ls -1 (note that's a one, not an L) may have been aliased for ls.

---

### Post by bodhi.zazen on 2007-08-28
Use the -C flag : 

so, change > alias ls='ls --color=auto'

to ```
alias ls='ls -C --color=auto'
```

Then 

```
source ~/.bashrc
```

---

### Post by Jamesbowden on 2007-08-28
> **bodhi.zazen said:**
> Use the -C flag : 

so, change 

to ```
alias ls='ls -C --color=auto'
```

Then 

```
source ~/.bashrc
```

Thank you, that seems to have worked, I'm not entirely sure what caused it in the first place.

---

### Post by pmg on 2007-08-29
> Thank you, that seems to have worked, I'm not entirely sure what caused it in the first place.
One possibility: if **ls** thinks it's not writing to a terminal but instead to a pipe to another program, or to a file, it changes it's default behavior and only writes one filename per line.  The **-C** flag overrides this behavior.

---

