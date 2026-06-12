---
title: "[SOLVED] GDM/Gnome login crash due of bash_completion"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by unutbu on 2008-03-12
I'm running Gutsy Gibbon.
Logging in through GDM/Gnome was working fine.

Then I do the following:
```

cp ~/.bashrc ~/.bashrc-orig
cp /etc/skel/.bashrc ~/.bashrc

```

I shut off the machine, power up, get to the gdm login prompt, login. Gutsy tells me my X session quit in <10 secs, and kicks me back to the gdm login prompt.

So I press CTRL-ALT-F2, login, and I comment out the lines in .bashrc regarding bash_completion:

```

#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

```

I power down, power up, and everything is once again hunky-dory.

How can I fix this so that I have bash_completion working?


Here is the surprisingly normal yet troublesome .bashrc:

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
    PS1='\t ${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='\t ${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
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

```

---

### Post by glennric on 2008-03-12
It is possible that the file /etc/bash_completion has been corrupted, or one of the files that it sources in /etc/bash_completion.d/.
Try "sudo apt-get install --reinstall bash" and see if that helps.  If not you may need to check the files in /etc/bash_completion.d.  Those belong to other packages.  You could try commenting out the section of the file /etc/bash_completion that sources those files (lines 9281-9288) and see if things work then.  If so you will have to figure out which file in there is causing the problem.  

You could also try booting with the bash_completion disabled (as you are now) and type
```
. /etc/bash_completion
```
after booting and see if that shows any errors.

---

### Post by unutbu on 2008-03-12
Yes, I forgot to mention: bash_completion seems to work if I type

```

. /etc/bash_completion

```

from the CLI, instead of the .bashrc.

---

### Post by unutbu on 2008-03-12
The good news is I narrowed down the problem somewhat. The bad news is, I don't know what to do about it.

Here is what I've tried:
```

sudo apt-get install --reinstall bash

```
No error messages. bash_3.2-0ubuntu11_i386.deb was re-installed.

Then I un-commented the three bash_completion lines from .bashrc.
Rebooted.
Same error.

This time, when warned that my xsession lasted <10 secs, I read the entire error message (doh) which suggested I have a peak inside ~/.xsession-errors:

Here is .xsession-errors:
```

(process:5965): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5969): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/home/cyrano/.bashrc: 15: shopt: not found
/etc/bash_completion: 48: Syntax error: Bad substitution

```

Is it the last two lines which indicate the problem?
First, why can't shopt be found? 

Line 15 of .bashrc:
```

shopt -s checkwinsize

```

and 
```

15:13:21 cyrano@farmer:~$ shopt
...
checkwinsize    on
...

```

Second, what to do about the 'syntax error: Bad substitution'?

Here are lines 42--54 of my /etc/bash_completion. (The 'if' statement is line forty-eight):
```

UNAME=$( uname -s )
# strip OS type and version under Cygwin (e.g. CYGWIN_NT-5.1 => Cygwin)
UNAME=${UNAME/CYGWIN_*/Cygwin}
RELEASE=$( uname -r )

# features supported by bash 2.05 and higher
if [ ${BASH_VERSINFO[0]} -eq 2 ] && [[ ${BASH_VERSINFO[1]} > 04 ]] ||
   [ ${BASH_VERSINFO[0]} -gt 2 ]; then
	declare -r bash205=$BASH_VERSION 2>/dev/null || :
	default="-o default"
	dirnames="-o dirnames"
	filenames="-o filenames"
fi

```

---

### Post by unutbu on 2008-03-13
The problem has been solved.

My .profile was calling .bashrc willy-nilly. It should have read
```

if [ -n "$BASH_VERSION" ]; then        #<---- This is the line I lacked
# Get the aliases and functions
    if [ -f ~/.bashrc ]; then
	. ~/.bashrc
    fi
fi

```

Thus, .bashrc was being called every time I logged in thru GDM. That should not happen.

Lesson learned: When porting a home directory from a different linux distro, DO NOT blindly copy the old .bashrc and .profile.

---

