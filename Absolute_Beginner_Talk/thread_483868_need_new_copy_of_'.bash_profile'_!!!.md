---
title: "need new copy of '.bash_profile' !!!"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by ColmOsiris on 2007-06-25
Help!

I was following a Linux tutorial, which showed me how to add an alias and a function to '.bash_profile' so that they would be available every time I log on.

It then said it was considered bad practice, and they should really be put in '.bashrc'.

Why it just didn't say put them there in the first place, I don't know!

Anyway, in trying to delete the new stuff from '.bash_profile' I deleted too many lines without realising I had done it. Consequently when I next logged in, I got this message about '.bash_profile' -

> line 1: syntax error near unexpected token `('

So I need to get back to my original copy of 'bash_profile'.

Please can someone tell me where I can get one.

I've got Ubuntu Server 6.10 with no GUI.

---

### Post by rax_m on 2007-06-25
Here is my original .bash_profile from my ubuntu feisty install. It shouldnt really be any different in edgy. 

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

---

### Post by ColmOsiris on 2007-06-25
That's brilliant, thanks. Seems all I'd deleted was the hash at the start of line 1!

---

### Post by nick_h on 2007-06-25
I think you will find a copy in /etc/skel - this is where adduser takes a copy for new users.

---

### Post by ColmOsiris on 2007-06-25
Thanks. I'll bear that in mind if I do anything silly again!

---

