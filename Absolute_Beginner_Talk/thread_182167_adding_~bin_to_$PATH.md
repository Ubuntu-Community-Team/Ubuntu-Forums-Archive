---
title: "adding ~/bin to $PATH"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by mlind on 2006-05-25
I'd like to add every user's ~/bin directory to existings PATH definition.

~/.bash_profile contains this snippet that shoud do it
```

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
   PATH=~/bin:"${PATH}"
fi

```

But if I add this to /etc/environment, it doesn't seem to work. (Maybe I should try with
$HOME/bin too..) Where should it put that code so I could get user's possible bin
directory on PATH?

---

### Post by colo on 2006-05-25
You forgot to `export` the variable - this way it won't be available in Subshells.

---

### Post by mlind on 2006-05-25
[QUOTE=colo]You forgot to `export` the variable - this way it won't be available in Subshells.[/QUOTE]

hmm. take a look at /etc/environment. I'm just appending it to existing PATH
that's defined on line 1 of that file.

I don't think ~/ is resolved correctly yet when environment variables are being
read from this file. I recall seeing erros about this on /var/log/messages

---

### Post by uzi09 on 2006-05-25
isn't everything in your home folder in the path by default??

---

### Post by mlind on 2006-05-25
[QUOTE=uzi09]isn't everything in your home folder in the path by default??[/QUOTE]

nope, at least not in my box. try *echo $PATH* to see youself.
I guess each of the PATH directories must be defined separately.

---

### Post by mlind on 2006-05-27
*bump*

---

### Post by mlind on 2006-05-30
hmm, anyone?

---

### Post by zman58 on 2006-06-20
I noticed in Dapper that even though I have a ~/bin statement in .bash_profile like so:

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

This entry in .bash_profile does not do any good when using graphical display manager interface (GDM - the desktop).

To get ~/bin directory in my path I created the file ~/.gnomerc and placed the lines above in that. Now whenever I log into the gnome desktop, my ~/bin directory is included in my $PATH environment. Voila! :)

---

### Post by mlind on 2006-06-25
I'll try using ~/.gnomerc too.
Thanks!

---

### Post by larryni on 2006-07-02
[QUOTE=zman58]To get ~/bin directory in my path I created the file ~/.gnomerc and placed the lines above in that. Now whenever I log into the gnome desktop, my ~/bin directory is included in my $PATH environment. Voila! :)[/QUOTE]
Thanks for that, been trying to figure this out for the past hour.

---

### Post by curtisf14 on 2006-07-12
Does anyone know the order in which login scripts run in Ubuntu (using Gnome and bash)?  This would be useful to know for the future.  Also, is there a way to change the order in which these scripts run?

---

### Post by mlind on 2006-07-12
> **curtisf14 said:**
> Does anyone know the order in which login scripts run in Ubuntu (using Gnome and bash)?  This would be useful to know for the future.  Also, is there a way to change the order in which these scripts run?

You can find this on bash manual page, line 93 and onwards.
```

man bash

```

---

### Post by curtisf14 on 2006-07-12
That helps, thanks.  However, "man bash" only tells me in which order bash runs scripts (which is pretty simple).  If this were the end of the story, then my PATH environment variable would be set correctly each time I log in, but it is not.  I have tried putting "export PATH=$PATH:'~/bin'" into both .bash_profile and .bashrc just to be sure, but when I open a terminal and check the variable, it does not include that directory.  Yes, my default shell is bash, and I have tried setting other variables in .bash_profile and .bashrc and it works fine.  Therefore I'm trying to figure out what is setting the PATH variable after those files run, or if my problem lies elsewhere.

---

### Post by mlind on 2006-07-12
> **curtisf14 said:**
> That helps, thanks.  However, "man bash" only tells me in which order bash runs scripts (which is pretty simple).  If this were the end of the story, then my PATH environment variable would be set correctly each time I log in, but it is not.  I have tried putting "export PATH=$PATH:'~/bin'" into both .bash_profile and .bashrc just to be sure, but when I open a terminal and check the variable, it does not include that directory.  Yes, my default shell is bash, and I have tried setting other variables in .bash_profile and .bashrc and it works fine.  Therefore I'm trying to figure out what is setting the PATH variable after those files run, or if my problem lies elsewhere.


For interactive non-login shells, like gnome terminal, only .bashrc is sourced. Put this on ~/.bashrc and make sure that ~/bin directory acually exists.

```

if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

```


The problem I was trying to tackle is to get ~/bin included on stage where the login shell (gnome or tty's) would actually read it too. For login tty's ~/.bash_profile works, but gnome doesn't seem to read these files.. So I need to use .~/gnomerc.

---

### Post by professor_chaos on 2006-07-12
Have you tried adding that code to ~/etc/bash.bashrc
This is supposed to make system wide changes for interactive shells

---

### Post by mlind on 2006-07-12
> **professor_chaos said:**
> Have you tried adding that code to ~/etc/bash.bashrc
This is supposed to make system wide changes for interactive shells

Duh.. That's probably the only file I didn't try back then. I think I should test if $HOME is already known when that file is sourced.

.gnomerc works only single user system though.


Thanks for the tip.

---

### Post by curtisf14 on 2006-07-12
Thanks for the info.  Works great!

---

