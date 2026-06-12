---
title: "bash_profile"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by meney on 2007-04-24
Hey all,

I'm doing some learning on the command line and I discovered that I do not have a .bash_profile file in my home directory. Is this file in another place in ubuntu? Will it hurt if I am to create one (is there anything important I need to include?).

Thanks!

---

### Post by amohanty on 2007-04-24
It wont hurt, but I think if you have some settings in a .bashrc file those will not load unless .bashrc is sourced from the .bash_profile. I could be off on that though.


The contents of mine are:
> if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

HTH
AM

---

### Post by LaurelLynn on 2007-04-24
.bash_profile does not exist by default since it is only for user customization.  So, you have to create it before it will be there.

---

### Post by meney on 2007-04-24
Cool thanks everybody!

So what is the real use of .bash_profile if you can just put the info in .bashrc? Just for organization sake?

Regards,

---

### Post by LaurelLynn on 2007-04-24
.bash_profile  -   runs only from login shells (such as at startup).

.bashrc -  runs **every** time you open a shell which doesn´t ask you to login in. Like Gnome terminal windows.

---

