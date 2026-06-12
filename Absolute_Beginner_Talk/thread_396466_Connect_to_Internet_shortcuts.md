---
title: "Connect to Internet shortcuts"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by dfreidus on 2007-03-29
Hi,

I have a small problem. I would like a shortcut for my internet connection to connect and disconnect to and from the internet. Currently, I have to open a terminal and type in "sudo ifup/ifdown ib0" and then type in a password. I tried to create a launcher but this only works when I set it to open in a terminal and then I still have to type my password. Is there a way to do this automatically, just clicking on a shortcut without any inputting anything further?

Thanks in advance for any help.

---

### Post by zvacet on 2007-03-29
You can type 
```
pon dsl-provider
```

but if you set up your connection correctly it sould work automaticly.

---

### Post by dfreidus on 2007-03-30
Thanks for the reply.

The connection does come on automatically when I turn on the computer. The thing is, is that we have very limited bandwidth and that I don't want it to clock up when I'm not on the computer. Therefore I often log in and out again. So my original problem still exists. Thanks very much for the help.

---

### Post by yigals on 2007-04-04
The best way I can think of, is adding the commands you use to connect/disconnect to the alias, and then you'll have a short command to put in the Alt+F2 command line.

You can do it as follows:
add the command you use to connect to this file:
~/.bash_profile

so for me it would be:
echo alias dc='poff -a' >> ~/.bash_profile

so now after pressing Alt+F2, just type 'dc' to disconnect
You can do the same for connecting:

echo alias cn='sudo pon dsl-provider' >> ~/.bash_profile

---

### Post by dfreidus on 2007-04-11
Hi, thanks for your reply - sorry it's taken me so long to respond.

I tried to do what you said, my .bash_profile file looks like this:

```
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

alias cn=sudo ifup ib0
alias dc=sudo ifdown ib0

```

but when i use the alt f2 to run i type it says that it could not open location. 

Thanks again very much for your help.

---

