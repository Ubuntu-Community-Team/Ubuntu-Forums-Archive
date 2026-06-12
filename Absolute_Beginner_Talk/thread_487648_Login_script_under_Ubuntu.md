---
title: "Login script under Ubuntu"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Explode2 on 2007-06-29
Hi guys, I'll just wanted to know, where I can find the login script under ubuntu feisty fawn 7.04..
I wanted to install the psp-dev, So its requerering, to set two enteries in the login script...with google and  this forum I'll didnt find anything(I'll think I am just using the wrong keywords..)
So'll maybe someone could give me an quick answer?
thanks a lot in advance,

Regards, Explode2

---

### Post by yota on 2007-06-29
Indeed there's nothing called "login script" on ubuntu.
The maximum likeness item could be "startup programs" under system/preferences/sessions, that is used to specify programs that are automatically started when a user's graphic session begins.

If I may ask: what are you installing exactly? If you write an url for the software we can help more!

---

### Post by Explode2 on 2007-06-29
Of course you can ask yota :)
this one I want to install:
[http://ps2dev.org/psp/Tools/Toolchain/psptoolchain-20070626.tar.bz2](http://ps2dev.org/psp/Tools/Toolchain/psptoolchain-20070626.tar.bz2)
It's not a link to a html file...
So I just got all packages, I installed it one time on my windows systems, but
since a year around I am nearly using only ubuntu...(because my windows systems all got crashed) ;)
So this last thing is, this login script thing, If I'll know where I *should* make there an entery in the system, I could programm my psp again :)

So thanks for the fast reply yota ;)

---

### Post by yota on 2007-06-29
> **Explode2 said:**
> 
So thanks for the fast reply yota ;)

You're welcome,

ok, now i got it, the site says:
> 
 2) Add the following to your login script:

  export PSPDEV=/usr/local/pspdev
  export PATH=$PATH:$PSPDEV/bin

So basically you need to set a new environment variable (PSPDEV) and update your path.

User environment is usually managed via .bash_profile file (or .bashrc), located in the home directory, so use them to set environment variables to your user only; otherwise use /etc/profile instead to set the variables system wide.

So make your choice and put there the commands suggested.

Hope this helps!

---

### Post by Explode2 on 2007-06-29
thanks again yota :)
uhm the problem is for me, I didnt find some file, calles .bash_profile or .bash_soul in my home directory (soul is my username)
so I'll think I'll make one...so there s the next problem:(
I do not know how some .bash_profile basically looks, so it would be very helpfull, if someone posts here the basic contents of some .bash_profl, so I could just copy and paste it and add the PSPDEV lines, and all would be ok and fine :)
:D

---

### Post by yota on 2007-06-29
Defaults are located in /etc/skel/ and should have been automatically copied by the installation procedure to your home; anyway this is .bash_profile
> 
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


---

### Post by Explode2 on 2007-07-01
Now its working :p
currently its installing..so after that I can programming my psp again :D

Thanks a lot yota ;)

---

