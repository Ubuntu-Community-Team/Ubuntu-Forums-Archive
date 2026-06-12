---
title: "File-type Colors in terminal"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by AJL on 2007-03-20
PLEASE forgive the absolute newb question...

I normally feel quite comfortable searching for myself, but in this case I don't know what to search for.

On every single one of my past installs I have had color "coded" names for files...like executables were a certain color, sym links were a color, etc, etc... 

Now, everything is just white text.  I can see where to change font color,  background color, etc but not a way to "turn on" the color coding in my terminal(s).

I am running Kubuntu 6.10 and have the issue in both Konsole and Gnome Terminal.


Please help!

Thanks,
Aaron

---

### Post by newlinux on 2007-03-20
does

```
ls --color=auto
``` do what you want?

---

### Post by AJL on 2007-03-20
> **newlinux said:**
> does

```
ls --color=auto
``` do what you want?

YES!  Now how do I make it  "stick"?

Thanks!

---

### Post by Efwis on 2007-03-20
thats what they are looking for, I was curious about this also. The only question now, is how to make it work that way permanently. it appears to only work when you run the command each time. This would be nice to have happen every time.

beat me to it :)

---

### Post by newlinux on 2007-03-20
you would need to set up an alias. If you are running the bash shell (which I believe is the default):

```
alias ls='ls --color=auto'
```

Put this command in your ~/.bashrc and every time you open up a terminal ls will be aliased to ls --color=auto.

---

### Post by mcduck on 2007-03-20
> **AJL said:**
> YES!  Now how do I make it  "stick"?

Thanks!

I have in my ~/.bashrc following piece of code:

```
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi
```

It's there by default, but if the colors are not working you could check if it's there or not..

---

### Post by ardchoille42 on 2007-03-20
There's a section near the bottom of ~/.bashrc that you can uncomment to have colors in your output.

---

### Post by newlinux on 2007-03-20
I would put the command at the end of your .bashrc file, BTW, for clarity.

---

### Post by AJL on 2007-03-20
What else do you have in your ~/.bashrc file?  Apparently mine is missing altogether.

---

### Post by AJL on 2007-03-20
> **mcduck said:**
> I have in my ~/.bashrc following piece of code:

```
[# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi/CODE]

It's there by default, but if the colors are not working you could check if it's there or not..

is this code example typo'd?  like, should there be an 
``` at the end to post a code block in the forum, or is that exactly how it should be in the bashrc?

---

### Post by Efwis on 2007-03-20
open Gedit and paste this in it.
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
    alias dir='ls --color=auto --format=vertical'
    alias vdir='ls --color=auto --format=long'
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
Then save as .bashrc
This will do exactly what you want done, modification is already complete.

---

### Post by newlinux on 2007-03-20
that's odd that you don't have a .bashrc. are you sure you are running the BASH shell?

what does:

```
echo $SHELL
```

return?

also what does:

```
slocate bashrc
```

return?

---

### Post by AJL on 2007-03-20
the echo returns 
/bin/bash

the slocate shows a .bashrc for root, but not me

---

### Post by AJL on 2007-03-20
thanks for the new bashrc EFwis, that worked like a charm.

and thanks to everybody else for their assistance!

---

### Post by newlinux on 2007-03-20
> **AJL said:**
> the echo returns 
/bin/bash

the slocate shows a .bashrc for root, but not me


Well, at least we know you are running bash. Using the previous poster's .bashrc should work for you then. Still odd that you don't have one...

---

### Post by Efwis on 2007-03-20
no problem, I was wondering about that myself, but in time I forgot to continue my search lol.

---

### Post by EnthropyinAction on 2007-12-18
Soooo . . . what's it mean if your .bashrc has that alias in it and still doesn't work?  Typing the full command at the prompt (ls --colors=auto) colorizes everything correctly, but the alias doesn't.

I'm using Debian now instead of Ubuntu,(and I know this should be on a Deb board, but this showed up first when I googled and I figured it'd be applicable) but the bash config should be universal, right?  Are the rules / syntax for the root .bash rc different?  Adding the alias worked for a user account, but when I su to change things (when the colors would be immensely more useful) they go away.  Even just adding the alias on its own doesn't work.

Oh, and for reference, what does the "if [ "$TERM" != "dumb" ]; then" do? I understand the if statement, but what's the condition mean?

---

