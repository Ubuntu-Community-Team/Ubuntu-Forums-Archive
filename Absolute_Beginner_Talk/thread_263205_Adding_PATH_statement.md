---
title: "Adding PATH statement"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-09-22
Check if Already Posted returned:
1. Sorry - no matches. Please try some different terms. 

I can't find: man path, setpath, or similar terms.


According to the WvDial FAQ, [http://open.nit.ca/wiki/index.php?page=WvDialFAQ](http://open.nit.ca/wiki/index.php?page=WvDialFAQ)  I should try to add information to the PATH, specifically the following line:

/usr/local/bin 

I have a paste of:  /root/.bashrc below.

Where exactly do I paste: /usr/local/bin
Does it need the term: [COLOR="DarkOrange"]PATH[/COLOR] or [COLOR="DarkOrange"]Path[/COLOR] or[COLOR="DarkOrange"] path[/COLOR] in it?
and
Worst of all, is this the right file? I don't see the word [COLOR="DarkOrange"]path[/COLOR] anywhere in it.


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


All this to resolve the "Cannot set information for serial port." Yikes! it's scary.

---

### Post by maaronB on 2006-09-22
/usr/local/bin should already be in PATH.  
To check open a terminal and type   
```
echo $PATH
``` 
it will give a list seperated by :'s it should look something like 
/usr/local/sbin:_/usr/local/bin_:/usr/sbin:/usr/bin:/sbin:/bin

---

### Post by kidcharles on 2006-09-22
Try adding this to .bashrc:

```
PATH=$PATH:/usr/local/bin
export PATH
```

Note at the top is says for "non-login" shells, which will include terminals you open up in Gnome, but not the full screen text-only login terminals you access with Ctrl-Alt-F1 through F6. There's a different config file for those, can't remember what it is though. More than a little strange that /usr/local/bin is not in the $PATH already.

---

### Post by Mark_in_Hollywood on 2006-09-24
> **maaronB said:**
> /usr/local/bin should already be in PATH.  
To check open a terminal and type   
```
echo $PATH
``` 
it will give a list seperated by :'s it should look something like 
/usr/local/sbin:_/usr/local/bin_:/usr/sbin:/usr/bin:/sbin:/bin

mark@Lexington:~$ echo path
path
mark@Lexington:~$

is all that was returned

---

### Post by maaronB on 2006-09-24
> **Mark_in_Hollywood said:**
> mark@Lexington:~$ echo path
path
mark@Lexington:~$

is all that was returned

try

```
echo $PATH
```

not 
echo path

PATH is not a program, it is an enviorment variable.

---

### Post by Mark_in_Hollywood on 2006-09-24
yikes!

mark@Lexington:~$ path
bash: path: command not found
mark@Lexington:~$

---

### Post by maaronB on 2006-09-24
> **Mark_in_Hollywood said:**
> yikes!

mark@Lexington:~$ path
bash: path: command not found
mark@Lexington:~$

PATH is not a command.  It is an eviorment variable.  It is the list of places that commands are stored.  
So when you typed in "path" it opened your PATH variable and checked in every one of the locations on the list for an executable statement called path.

But path is not an executable statement, PATH (capitalization matters in linux) is a list of locations to check.

To use the contents of a variable on your system.  You need to type  a $ (dollar sign) followed by the variable name with no space between.

So what you want to do is see the value that is stored in the variable PATH (capitalized).

to do this you type

echo $PATH   <capitalized and with a doller sign in front of it.>

do not type
echo path
echo PATH
echo $path
echo $ path
echo $ PATH
echo path$ 
echo Path

Also I can guarantee you that /usr/local/bin is already in your PATH.

---

### Post by Mark_in_Hollywood on 2006-09-24
Sorry for not prefacing all of the foregoing with NEWBIE!


Still:

mark@Lexington:~$ PATH
bash: PATH: command not found
mark@Lexington:~$

---

### Post by Mark_in_Hollywood on 2006-09-24
oooppss!! I thought I saw a $

mark@Lexington:~$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games: No such file or directory
mark@Lexington:~$

---

### Post by maaronB on 2006-09-24
> **Mark_in_Hollywood said:**
> Sorry for not prefacing all of the foregoing with NEWBIE!


Still:

mark@Lexington:~$ PATH
bash: PATH: command not found
mark@Lexington:~$

when you type something in to a terminal it "believes" that the first word is a command.  
What it is telling you is that PATH in not a command.  We know that already, it is a variable.

[I](A variable is a value stored under a name,
for instance if you typed X=203756
then $X could be used instead of typing 203756.
so if you typed 
echo X
you would see on the screen
X
if you typed echo $X
you would see
203756.

This is because you use the doller sign ($) to return the value stored in the variable.  If it is ommited you just return the variable name.)[/I]

echo is a command.  It causes whatever follows it to be printed to the screen
So if you type 
```

echo "My name is Mark"

```
you will see
My name is Mark


so if you type 
```

echo PATH

```

you will see the word
PATH 
printed to to the screen

This is **NOT** what we want. 
What we are trying to do is get it to print the value stored in the variable PATH.
To do that we place a Doller Sign ($) in front of PATH
this will cause it to be viewed as the value stored in PATH.
so you type 
```

echo $PATH

```
you have to include the 
echo 
statement in there because that is the command that we are using to print to the screen.

**TYPE:**
```

echo $PATH

```

that will give you the value stored in PATH.

---

### Post by maaronB on 2006-09-24
> **Mark_in_Hollywood said:**
> oooppss!! I thought I saw a $

mark@Lexington:~$ $PATH
bash: /usr/local/sbin:**/usr/local/bin**:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games: No such file or directory
mark@Lexington:~$

/usr/local/bin is already in your PATH.

---

### Post by Mark_in_Hollywood on 2006-09-24
mark@Lexington:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
mark@Lexington:~$


so, where did you learn about this? 

mark@Lexington:~$ man path
No manual entry for path

mark@Lexington:~$ man variable
No manual entry for variable

mark@Lexington:~$ man environment
No manual entry for environment

---

