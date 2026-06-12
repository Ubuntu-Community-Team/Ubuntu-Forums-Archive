---
title: "[URGENT]Proxy in Terminal"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2006-11-27
I am using the same proxy settings in System>>Preferences>>Network Proxy as i using in firefox, but firefox is working but if i try to use wget from terminal it says:

--14:16:02--  [http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz)
           => `easyubuntu-3.023.tar.gz'
Connecting to 172.30.10.10:3128... connected.
Proxy request sent, awaiting response... 407 Proxy Authentication Required
14:16:02 ERROR 407: Proxy Authentication Required.


I don't know where the problem is.
Need urgent solution.

---

### Post by Bachstelze on 2006-11-27
[http://www.progsoc.uts.edu.au/lists/slug/2000/June/msg00204.html](http://www.progsoc.uts.edu.au/lists/slug/2000/June/msg00204.html)

---

### Post by shoaibi on 2006-11-27
> **HymnToLife said:**
> [http://www.progsoc.uts.edu.au/lists/slug/2000/June/msg00204.html](http://www.progsoc.uts.edu.au/lists/slug/2000/June/msg00204.html)

i am just a newbie, need a short and complete and easy way :(

---

### Post by Bachstelze on 2006-11-27
could you please paste the ouput of :

```
cat ~/.bashrc
```

and

```
echo $http_proxy
```

---

### Post by shoaibi on 2006-11-27
of the first command:

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



of second command:
[http://172.30.10.10:3128/](http://172.30.10.10:3128/)

---

### Post by Bachstelze on 2006-11-27
All right, do this :

```
export http_proxy='http://YOUR_USERNAME:YOUR_PASSWORD@172.30.10.10:3128/'
```

---

### Post by shoaibi on 2006-11-27
sorry!

---

### Post by daschl on 2006-11-27
> **shoaibi said:**
> sorry!

what do you mean with that? is it working for you with HymnToLife's solution? :)

---

### Post by shoaibi on 2006-11-27
and how to de-activate this proxy?

---

### Post by Bachstelze on 2006-11-27
```
unset http_proxy
```

---

### Post by argie on 2006-11-27
I had this problem too. In Dapper the proxy settings in System > Prefs > Network Proxy are fine but the authentication details don't go through. Setting the username:password@host works there too.

---

### Post by salariua on 2007-11-12
That did it for me but I had to put ... 

export http_proxy='192.168.0.2:3128/

since there is no user name or password.

10x

---

### Post by shoaibi on 2007-11-16
well the new versions of ubuntu don't need all that export of enviornmental variables, i just put my proxy in the network settings in preferences and its globally accessible, on terminal, in synaptic, everywhere, unlike before....

I don't think anyone will face these kinds of problems anymore.

SOLVED!

---

### Post by juky on 2008-07-09
Thanks, wget works for me now!

---

