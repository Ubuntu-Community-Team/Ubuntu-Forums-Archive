---
title: "bash problem"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by adilici on 2007-03-22
Hi.

I'm a complete beginner in anything that has to do with linux and it should become quite obvious pretty soon...

Here's my problem. I had to do some java work and javac wouldn't be recognized without the full path. So i read around i found out that i had to add some lines to .bashrc... I opened it in gedit using # gedit /.bashrc

The disaster was a power failure while the file was open. I did not even get to make any changes, much less save them, but now, whenever i open a terminal window i get a list of bash errors as follows :

bash: lesspipe: command not found
bash: dircolors: command not found
bash: uname: command not found
bash: uname: command not found
bash: [: !=: unary operator expected
bash: [: too many arguments
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: too many arguments
bash: [: =: unary operator expected
bash: sed: command not found

Of course, i get "command not found" for any command i give and i have to use the full path for everything now. 

Therefore, any help is appreciated.

I use Ubuntu 6.06 i386.

Thanks.

---

### Post by Bachstelze on 2007-03-22
```
/bin/echo $PATH
```

what does that give you ?

---

### Post by adilici on 2007-03-22
/usr/lib/java/jdk1.6.0/bin/javac

---

### Post by Bachstelze on 2007-03-22
Do you see any lines regarding this in either /etc/bashrc or ~/.bashrc ?

---

### Post by adilici on 2007-03-22
Yes, there were 2 i had added in bash.bashrc that didn't give me any problem until i opened ~/.bashrc. I deleted them and I'm back to normal. Thanks a lot!

Since we're here, can you give me a safe way to set up bash so that it recognizes javac?

---

### Post by Bachstelze on 2007-03-22
In your ~/.bashrc, I guess you put

```
export PATH='/usr/lib/java/jdk1.6.0/bin/javac'
```

that wasn't the right thing to do, as you can see, it overrid the old $PATH ans set it instead. To just add it to your $PATH, add this line in one of the bashrc's :

```
export PATH='$PATH:/usr/lib/java/jdk1.6.0/bin/'
```

---

### Post by adilici on 2007-03-22
Thank you very much once again. It worked like a charm.

---

### Post by adilici on 2007-03-22
Sorry to come back with this, but apparently there's still a problem.

If I add the line you suggested to ~/.bashrc when i'm logged in as a certain user (including root) i lose  all other command paths except cd, mv and such. They still work with other users.

I would give this up, but unfortunately i have to use a simulator that runs javac and it would be infinitely more dificult to edit it.

---

### Post by Bachstelze on 2007-03-22
Please paste the contents of ~/.bashrc and the output of *echo $PATH*.

---

### Post by adilici on 2007-03-22
~/.bashrc :

```

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

export PATH='$PATH:/usr/lib/java/jdk1.6.0/bin/'

```

and for echo $PATH

```

adi@Powerstation:~$ echo $PATH
$PATH:/usr/lib/java/jdk1.6.0/bin/

```

---

### Post by Bachstelze on 2007-03-22
Sorry, my mistake... In the line I told you to put in your bashrc, replace the single quotes ' with doulble-quotes ". As you can see, using single quotes put $PATH litterally into the varialbe instead of replacing it with it's value.

---

### Post by adilici on 2007-03-22
Indeed, now everything works just fine. Thank you very much for taking the time.

---

