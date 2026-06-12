---
title: "&quot;less&quot;   and &quot;sux&quot; commands are creating problems!!"
date: 2008-03-13
forum: Arch and derivatives
---

### Post by deepclutch on 2008-03-13
Hai,
well in my other distro(debian) "less" command in terminal(gnome terminal) allows "scrolling" using mouse's middle wheel.
but,I am missing this option in archlinux's less.what can be a solution 

I need the scroll option somehow :(
although I can scroll through terminal(konsole) output easily.

another problem.
I am used to a xwrapper to "su" called "sux" which is available in AUR.
when I open a terminal and run sux -gave root password,I can login fine.
but all shell (environment) variables are pretty fcuked up.
while in a normal shell or as "su",I am getting below shell variables:
```
prakash ~  $  echo $PATH
/bin:/usr/bin:/sbin:/usr/sbin:/usr/X11R6/bin:/opt/bin:/opt/kde/bin:/opt/qt/bin:/opt/mozilla/bin/:/opt/qt/bin:/opt/kde/bin
```and:
```
prakash ~  $  su -
Password:
root ~ #  echo $PATH
/bin:/usr/bin:/sbin:/usr/sbin:/usr/X11R6/bin:/opt/bin:/opt/kde/bin:/opt/qt/bin:/opt/mozilla/bin/
```**But,as "sux:**
```
prakash ~  $  sux -
Password:
root ~ #  echo $PATH
/usr/ucb:/bin:/usr/bin:/etc
```Before guessing that I have to edit and append the PATH's in ~/.bashrc or ~/.bash_profile or /etc/profile or /etc/profile_bash ,I have tried all these :(

still,my /etc/profile looks as below:
```
oot ~ #  cat /etc/profile
#
# /etc/profile
#
# This file is intended to be used for ALL common
# Bourne-compatible shells. Shell specifics should be
# handled in /etc/profile.$SHELL where $SHELL is the name
# of the binary being run (discounting symlinks)
#
# Sections taken from SuSe's /etc/profile
# Note the explicit use of 'test' to cover all bases
#  and potentially incompatible shells

#Determine our shell without using $SHELL, which may lie
shell="sh"
if test -f /proc/mounts; then
   case $(/bin/ls -l /proc/$$/exe) in
        *bash) shell=bash ;;
        *dash) shell=dash ;;
        *ash)  shell=ash ;;
        *ksh)  shell=ksh ;;
        *zsh)  shell=zsh ;;
    esac
fi

# Load shell specific profile settings
test -f "/etc/profile.$shell" &&  . "/etc/profile.$shell"

#Set our umask
umask 022

# Set our default path
PATH="/bin:/usr/bin:/sbin:/usr/sbin"
export PATH

# Some readline stuff that is fairly common
HISTSIZE=1000
HISTCONTROL="erasedups"

INPUTRC="/etc/inputrc"
LESS="-R"
LC_COLLATE="C"

export HISTSIZE HISTCONTROL INPUTRC LESS LC_COLLATE

# Load profiles from /etc/profile.d
if test -d /etc/profile.d/; then
    for profile in /etc/profile.d/*.sh; do
        test -x $profile && . $profile
    done
    unset profile
fi

# Termcap is outdated, old, and crusty, kill it.
unset TERMCAP

# Man is much better than us at figuring this out
unset MANPATH

export PATH="/bin:/usr/bin:/sbin:/usr/sbin:/usr/X11R6/bin:/opt/bin:/opt/kde/bin:/opt/qt/bin:/opt/mozilla/bin/"
```and /etc/profile.bash
```
root ~ #  cat /etc/profile.bash
#
# /etc/profile.bash
# Global settings for bash shells
#

PS1='[\u@\h \W]\$ '
PS2='> '
PS3='> '
PS4='+ '

export PS1 PS2 PS3 PS4

#In the future we may want to add more ulimit entries here,
# in the offchance that /etc/security/limits.conf is skipped
ulimit -Sc 0 #Don't create core files

if test "$TERM" = "xterm" -o \
        "$TERM" = "xterm-color" -o \
        "$TERM" = "xterm-256color" -o \
        "$TERM" = "rxvt" -o \
        "$TERM" = "rxvt-unicode" -o \
        "$TERM" = "xterm-xfree86"; then
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME%%.*}:${PWD/$HOME/~}\007"'
    export PROMPT_COMMAND
fi

export PATH="/bin:/usr/bin:/sbin:/usr/sbin:/usr/X11R6/bin:/opt/bin:/opt/kde/bin:/opt/qt/bin:/opt/mozilla/bin/"
```My ~/.bash_profile:
```
root ~ #  cat .bash_profile
. $HOME/.bashrc
```and ~/.bashrc:
```
root ~ #  cat .bashrc
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

#fancy color prompt
PS1='\[\e[0;31m\]\u\[\e[m\] \[\e[1;34m\]\w\[\e[m\] \[\e[0;31m\]\$ \[\e[m\]\[\e[0;32m\] '


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

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi


#aliases
alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'

# some more ls aliases
alias ll='ls -l'
alias la='ls -A'
alias l='ls -CF'

# enable bash completion in interactive shells
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```So some help?:):)

Is both these problems due to wrong environment variables?
also, :
```
root ~ #  cat /etc/environment
#
# This file is parsed by pam_env module
#
# Syntax: simple "KEY=VAL" pairs on seperate lines

PATH="/bin:/usr/bin:/sbin:/usr/sbin:/usr/X11R6/bin:/opt/bin:/opt/kde/bin:/opt/qt/bin:/opt/mozilla/bin/"
LANG="en_US.utf8"
LANGUAGE="en_US.utf8"
PAGER=less
```Where what went wrong :(:(:(

Is below output helps?Please go through below and point me what is wrong :?
```
root ~ #  printenv
SHELL=/bin/bash
TERM=xterm
USER=root
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
PATH=/bin:/usr/bin:/sbin:/usr/sbin:/usr/X11R6/bin:/opt/bin:/opt/kde/bin:/opt/qt/bin:/opt/mozilla/bin/
PWD=/root
SHLVL=1
HOME=/root
LOGNAME=root
DISPLAY=:0.0
_=/usr/bin/printenv
```

---

### Post by deepclutch on 2008-03-14
this is weird,I googled and cant find a single solution! :cry:

---

