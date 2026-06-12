---
title: "help with .bash_profile edit"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by antonyant11 on 2008-03-30
Hi I need help editing paths in my .profile

I am trying to install maxwell render for maya and the instructions ask

------------------------------------------------------------------------------------------------

Define the following environment variables in your shell:

MAXWELL_ROOT="maxwell installation path"
LD_LIBRARY_PATH="maxwell installation path":$LD_LIBRARY_PATH

For example, if maxwell is installed in /opt/local/maxwell64-1.6 and you use BASH, add the 
following lines in $HOME/.bash_profile:

export MAXWELL_ROOT=/opt/local/maxwell64-1.6
export LD_LIBRARY_PATH=/opt/local/maxwell64-1.6:$LD_LIBRARY_PATH

--------------------------------------------------------------------------------------------------

I canot seem to find $HOME/.bash_profile but i can find $HOME/.profile I assume this is the .bash_profile for feisty fawn.   I have opened the file in kate and have editited it as follows

-------------------------------------------------------------------------------------------------------

# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f ~/.bashrc ]; then
	. ~/.bashrc
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"

fi

export MAXWELL_ROOT=/opt/local/maxwell64-1.6
export LD_LIBRARY_PATH=/opt/local/maxwell64-1.6:$LD_LIBRARY_PATH

------------------------------------------------------------------------------------------------------

this seems to have no effect after i reboot. (I still get path errors in maya)

Is this the correct way to do this?

thanks in advance:)

---

### Post by c-ron on 2008-03-30
> **antonyant11 said:**
> 
Define the following environment variables in your shell:

For example, **if** maxwell is installed in /opt/local/maxwell64-1.6 and you use BASH, add the 
following lines in $HOME/.bash_profile:

export MAXWELL_ROOT=/opt/local/maxwell64-1.6
export LD_LIBRARY_PATH=/opt/local/maxwell64-1.6:$LD_LIBRARY_PATH


Is maxwell installed in /opt/local/maxwell64-1.6 ?

A better place for this question might be the Maxwell forum: [http://www.maxwellrender.com/forum/](http://www.maxwellrender.com/forum/)

---

### Post by antonyant11 on 2008-03-30
yes it is installed in that location.

Unfortunatly I am not able to post on maxwell as yet...:(

---

