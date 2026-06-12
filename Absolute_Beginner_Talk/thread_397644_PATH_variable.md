---
title: "PATH variable"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by nick623 on 2007-03-30
I put my PATH variable in the .bash_profile then I gave it the export command.
I thought that doing this would make my PATH file available to any other new shell including a new terminal.

But when I open a terminal in gnome my PATH is not there.

Am I doing something wrong.

Thanks.

---

### Post by taurus on 2007-03-30
You need to add it to ~/.bashrc.

```
PATH=$PATH:next_path:and_another_path
export PATH
```

---

### Post by nick623 on 2007-03-30
Thanks.
My other computer uses Fedora and all I do is issue command "export PATH=$PATH:whateverpath" in the .bash_profile file and everything is fine.

I'm just wondering if this is an Ubuntu/Debian thing where I put everything in the .bashrc file to run in every other new shell.

Thanks

---

### Post by taurus on 2007-03-30
It's always ~/.bashrc even when I use Gentoo, Slackware/Zenwalk/VectorLinux, and FC6.

---

### Post by scxtt on 2007-03-30
.bash_profile is read by a login shell ... .bashrc is read anytime bash is invoked w/in a session ... so if you don't have .bash_profile source .bashrc, you'd have to do it yourself ...

---

### Post by ousp on 2007-03-31
i doubt that ~/.bashrc is the natural place to set your path as the default ubuntu ~/.bash_profile contains a PATH setting, PATH=~/bin:"${PATH}", but this setting does not reach gnome-terminal (checked centos-behaviour: after new X-login, PATH set in ~/.bash_profile is available to gnome-terminal)

---

### Post by martinbures on 2007-04-05
I am super-confused:

I tried to add something to my path and now it seems to be corrupted.  

Here is what I get:
martin@martin-laptop:~$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games: No such file or directory

If I type echo %PATH, I get this:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

all of these directories exist and I don't seem to have any problems with them.

I am trying to find the original PATH so that I can fix it and can't find it anywhere.  None of the files have PATH defined, just references to the environmental variable.

here is my ~/.bashrc:
martin@martin-laptop:~$ cat ~/.bashrc
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

here is my ~/.bash_profile
martin@martin-laptop:~$ cat .bash_profile
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

here is my /etc/profile:
martin@martin-laptop:~$ cat /etc/profile
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
        . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

here is my /etc/bash.bashrc:
martin@martin-laptop:~$ cat /etc/bash.bashrc
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
        cat <<-EOF
        To run a command as administrator (user "root"), use "sudo <command>".
        See "man sudo_root" for details.

        EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/bin/command-not-found ]; then
        function command_not_found_handle {
                /usr/bin/command-not-found $1
                return $?
        }


I am running Edgy.  Thanks for your responses to this super-noob question.

later.
martin.

---

### Post by scxtt on 2007-04-06
> martin@martin-laptop:~$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games: No such file or directoryyou want to do **echo $PATH**, not just $PATH ... using echo will display the contents of $PATH, not try to run each item in the $PATH variable (which is why you're getting **No such file or directory**) ...

afaik, your initial path is defined in /etc/login.defs --- ```
[font=courier]ENV_PATH          PATH=/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games[/font]
```

---

### Post by martinbures on 2007-04-07
Hey, thanks a lot!  That is exactly what I have been looking for.  Google is not very helpful, or maybe I was just asking the wrong questions.

Now I have to figure out why I am getting that error.  I have done what you said - I thought that I had posted that output.

Here it is:
martin@martin-laptop:~/Desktop/u-boot-1.1.6$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games: No such file or directory

martin@martin-laptop:~/Desktop/u-boot-1.1.6$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

and the output from /etc/login.defs:
#
# *REQUIRED*  The default PATH settings, for superuser and normal users.
#
# (they are minimal, add the rest in the shell startup files)
ENV_SUPATH      PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11
ENV_PATH        PATH=/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games

---

### Post by towanda on 2007-04-08
Martin, $PATH is being interpreted as a command.  When you just type **$PATH** at your shell prompt, it tries to run everything in your PATH as if they are all programs or files.  That's why you're getting the error.

If you want to list what is in your PATH, you need to type **echo $PATH** at the shell prompt.  That will display what is in your PATH without generating an error.

---

