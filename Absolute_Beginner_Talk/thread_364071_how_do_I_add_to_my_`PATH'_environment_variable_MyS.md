---
title: "how do I add to my `PATH' environment variable? MySQL Installation"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by HighD on 2007-02-17
Ok, so I'm installing MySQL 5.1 on Edgy and I need to do the following:

> 
The `bin' directory contains client programs and the server.
You should [B][I][U]add the full pathname of this directory to your
`PATH' environment variable so that your shell finds the MySQL
programs properly[/U][/I][/B].

The MySQL installation folder is /usr/local/mysql/ which has this bin directory, how do I add this pathname to this `PATH' enviroment variable?

I've researched a little and it seems it has to do with my .bash_profile file, which in my case is the following : 

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
```

So any suggestions? Thanks in advance for all your help ::mrgreen::

---

### Post by confused57 on 2007-02-17
Here's a similar discussion in the Gentoo forums:
[http://forums.gentoo.org/viewtopic-t-341909-highlight-environmental+variables.html](http://forums.gentoo.org/viewtopic-t-341909-highlight-environmental+variables.html)

>  use ~/.bashrc like this
export PATH=$PATH:/path_to_add

You also might want to read over this:
[http://www.lowfatlinux.com/linux-environment-variables.html](http://www.lowfatlinux.com/linux-environment-variables.html)

---

