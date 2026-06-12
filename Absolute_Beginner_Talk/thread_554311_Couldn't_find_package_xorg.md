---
title: "Couldn't find package xorg"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Eagle784 on 2007-09-18
I'm running Ubuntu 6.0.6 LTS on a remote i386 server in .de.  I get the error "couldn't find package xorg" when trying to install it via apt-get install xorg. I did apt-get update and apt-get upgrade with no effect.
 I have tried updating my sources.list as follows:
#Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted


# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://ax.archive.ubuntu.com/ubuntu](http://ax.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Upstream Wine
# GPG key: 387EE263
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main


still no luck.  

Does anyone have any ideas?  Thanks for any help you can give.  Also, this is my first time using Linux, so please be kind :)

---

### Post by alienexplorers on 2007-09-18
I looked in synaptic and can not find a package called xorg.  There is however a package called xorg-driver-fglrx.

---

### Post by Eagle784 on 2007-09-18
Oh the reason I ask is that I was following a tutorial and everyone's first instruction is to install xorg.  I've successfully installed gnome seemingly without a problem however.  Do you know why installing xorg might be recommended?  Also forgot to mention I tried this:

"to fix your problem, 

first, try to run the command 

sudo apt-get install xserver-xorg

not just xorg.. if it is alread y installed, then run the command

sudo dpkg-reconfigure xserver-xorg

and follow the prompts to configure your xserver. 
That should fix any xserver problems in Ubuntu... which has been notorious (as far as I can tell) with misconfiugring the xserver during the install."

except the second command wouldn't work ...

---

### Post by alienexplorers on 2007-09-18
What error do you get when you run;
> sudo dpkg-reconfigure xserver-xorg

What video card are you trying to configure and do you have the latest drivers installed.

---

### Post by Eagle784 on 2007-09-19
Oddly, I installed wine and ubuntu desktop, and now it works fine.

---

