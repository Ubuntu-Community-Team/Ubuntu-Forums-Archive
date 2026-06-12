---
title: "Change PATH permanently"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by jfinkels on 2007-03-14
Doing *export PATH=$PATH:/home/myusername/bin* will only change my path for that session in side the terminal. Once I exit the terminal, PATH is back to normal. Is there an elegant way to change it permanently without running a script at startup or something?

---

### Post by orkim on 2007-03-14
Typically this is done on a per user basis by editing the /home/user/.profile file and adding the line that you need.  If you want it to be for all users you would want to look at /etc/profile or /etc/environment.

Hope that helps.

-orkim

---

### Post by ufan on 2007-03-27
I noticed that .bash_profile adds ~/bin to PATH if the bin directory exists.  So I created a bin directory in my home directory.

After logging in and out, this still does not work.  However if I read in my profile manually it does. So this works (as it should):   . .bash_profile (now my private bin is in $PATH)

(I logged out and back in again, also rebooted to be sure)

Any ideas.

---

### Post by jfinkels on 2007-03-27
> **ufan said:**
> I noticed that .bash_profile adds ~/bin to PATH if the bin directory exists.  So I created a bin directory in my home directory.

After logging in and out, this still does not work.  However if I read in my profile manually it does. So this works (as it should):   . .bash_profile (now my private bin is in $PATH)

(I logged out and back in again, also rebooted to be sure)

Any ideas.

I also found the same problem when I was looking for a solution to my question above: ~/.bash_profile lies to me! The default ~/.bash_profile looks like this:
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

However, the last if statement fails to add my ~/bin directory to my PATH. So I settled for adding ~/bin in my ~/.profile . I would very much like to know why ~/.bash_profile fails to work as it says it was intended to work.

---

### Post by ufan on 2007-03-28
Perhaps we have stumbled across a little bug.

It seems that .bash_profile is not read by the gnome terminal at all.  .bash_profile itself is ok because as I said before, if we 'source' .bash_profile from a running terminal, we get the behaviour we want. (You will have to remove the path addition line from your .profile first to test it).

I wonder if gnome terminal is calling bash without the ```
--login
``` option as this option results in .bash_profile not being sourced.

I logged into a plain console after ```
Ctrl+Alt+F1
``` and my .bash_profile is read correctly and everything works as promised.  To get back to the GUI from the console, logout and go ```
Alt+F7
```.

I wonder if it is a bug?

---

### Post by jfinkels on 2007-03-29
Boy, would that be cool! I doubt it, though :P Maybe if somebody more knowledgable comes along we'll find out.

---

### Post by enerata on 2007-08-28
**For the others to see, and for my reference, I have done some changes to ~/.profile and ~/.bashrc so that profile gets parsed by ~/.bashrc when logging on via a dm (i.e. xdm, gdm, e.t.c.)**

# ~/.bashrc fix: If PROFILE_SOURCED is set we source the ~./.profile and
# exit because ~/.bashrc gets sourced by ~./.profile
if [ -z $PROFILE_SOURCED ]; then
    echo "Parsing ~/.profile"
    . ~/.profile
    return
fi

# ~./profile fix: If xdm is enabled then no login happens from the command
# prompt, and so ~./.profile does not get sourced. So we set PROFILE_SOURCED
# here and when ~./bashrc gets parsed and PROFILE_SOURCED is not set
# we source the ~./.profile file
export PROFILE_SOURCED=true

Regards.

---

### Post by asmoore82 on 2007-08-28
It is not a bug ... BASH is not invoked as a login shell from within GNOME-Terminal.

the most proper way to set up your BASH environment is to add the changes to your ~/.bashrc file
and then make sure that ~/.bash_profile sources ~/.bashrc in the event of a real login shell.

Ubuntu users have no ~/.bash_profile by default so you could make one that looks like this:
```
# .bash_profile

if [ -f ~/.bashrc ]; then
source ~/.bashrc
fi

# End of File
```

---

