---
title: "error in Xterm"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by harys on 2006-04-02
hi, i have this message when i open the xterm : 
bash: /home/harys/.bashrc: line 77: unexpected EOF while looking for matching `''
bash: /home/harys/.bashrc: line 80: syntax error: unexpected end of file
harys@harys:~$

what does it mean and how must i do to resolve it ?  thanks so much . harys.

---

### Post by siminone on 2006-04-02
It looks like there is something wrong with your bashrc file.

Can you please type in more more /home/harys/.bashrc and paste the output into a reply.

---

### Post by harys on 2006-04-02
hi, i've ran the command  more more /home/harys/.bashrc
  and here below is the reply : 

harys@harys:~$ more more /home/harys/.bashrc
more: No such file or directory
::::::::::::::
/home/harys/.bashrc
::::::::::::::
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

# my personal aliases
alias cp='cp -v -i
alias rm='rm -i'
alias mv='mv -i'
export ALSA_OUTPUT_PORTS="128:0"
export SCUMMVM_PORT=128:0
harys@harys:~$

thanks. harys

---

### Post by siminone on 2006-04-02
the problem is that there is a quote missing.

Enter the enter commands into terminal: 

cd $HOME
gedit .bashrc

In the alias section at end put in quote for the cp alias so that it looks like this: 

alias cp='cp -v -i'

Save the file, exit from terminal and open it up again.

---

### Post by harys on 2006-04-02
thank so much! i worked very well!!!!!! harys

---

