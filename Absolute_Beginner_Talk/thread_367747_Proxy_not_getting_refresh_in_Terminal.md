---
title: "Proxy not getting refresh in Terminal"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-22
i set my previous proxy as
export http_proxy ="http://fac097:963852@172.30.10.10:3182/"
in /etc/environment for being permanent.

now i want to change it to
export http_proxy="http://bs0426:47661477@712.30.10.11:3128/"

i changed it in the /etc/environment, even restarted GNOME by CTRL+ALT+BACKSPACE, and even restarted the system by rebooting, but this is what i get:
```

shoaibi@saber-rider:~$ echo $http_proxy
http://fac097:963852@172.30.10.10:3128/
shoaibi@saber-rider:~$ cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_US.UTF-8"
export http_proxy="http://bs0426:47661477@172.30.10.11:3128/"
shoaibi@saber-rider:~$ echo $http_proxy
http://fac097:963852@172.30.10.10:3128/

```


beisdes:

```

shoaibi@saber-rider:~$ unset $http_proxy
bash: unset: `http://fac097:963852@172.30.10.10:3128/': not a valid identifier
shoaibi@saber-rider:~$ 


```

---

### Post by netkid91 on 2007-02-22
Make sure it isn't being overwritten in your ~/.bashrc file.
Also, in unset you are putting in $http_proxy, get rid of the $, it is substituting the value of $http_proxy instead of the variable itself.

---

### Post by shoaibi on 2007-02-22
this is output of .bashrc:

```

shoaibi@saber-rider:~$ cat /root/.bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
#export HISTCONTROL=ignoredups

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" -a -r /etc/debian_chroot ]; then
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
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi


```

---

### Post by shoaibi on 2007-02-22
even used unset http_proxy and restarted. still no use...

---

### Post by netkid91 on 2007-02-22
> **shoaibi said:**
> even used unset http_proxy and restarted. still no use...
Using unset is only temporary, did you try removing the line from /etc/enviornment?

---

### Post by shoaibi on 2007-02-23
yup, i did paste the output of cat /etc/enviornment in my first post

---

