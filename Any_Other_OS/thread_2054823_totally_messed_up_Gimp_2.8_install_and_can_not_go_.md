---
title: "totally messed up Gimp 2.8 install and can not go back"
date: 2012-09-08
forum: Any Other OS
---

### Post by Warren North on 2012-09-08
In my Linux Mint 13 computer I tried to install mint just like all the websites said and so many said they were successful except myself.
I can not go back to 2.6 and synaptic no longer has the package.
I had to purged the old version and could not install the new one.
My question is it better to just to try to install it from the source file.
Like it a regular old fashion Linux install or wait till enough people have the 
same problem. So far I have searched and anyone with the same problem
is still stuck or get unstuck but I am still stuck. I have had PPA problems and the system has had issues with updating so I may have multiple problems that are the cause. Any help would greatly be appreciated. 
I been working thought the source.list and go some of that fixed.
Mint is funny as it needs some ubuntu stuff but seems to reject some of the repositories. 
In any case I got gimp on my 10.04 Ubuntu and 2.8 on my Arch machine so I am not in a hurry. But I got no where else to go. 90% of the time I been able to fix anything because some people do the same. This time I think I goofed and should of stayed with the notion that if it aint broke don't fix it.

---

### Post by lincoln32 on 2012-09-08
some of the newer mint's are based on debian and while the ubuntu stuff should work you may run into things like this. plus newest and latest can always be a issue/gamble. purge should remove all traces so you should be able to reinstall a older version. but log files and or more details would be needed to figure out your current issue):P

---

### Post by Epodx64 on 2012-09-08
Did you use "sudo apt-get purge gimp" or do you have the ppa-purge apt tool installed?

---

### Post by Warren North on 2012-09-08
warren@warren-SH61R4 ~ $ sudo apt-get install gimp
[sudo] password for warren: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gimp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gimp' has no installation candidate

Example of losing this package 

below are other info they may give clues


Sources.list
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) maya main upstream import
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
# deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise partner
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free

# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb apps
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb games


I tried commands like (not in this order but to purge then install)

 sudo apt-get purge gimp*
sudo apt-get clean
sudo apt-get remove gimp
sudo apt-get install -f
sudo apt-get install gimp=2.6.12-1ubuntu1
sudo apt-get update


At some point I almost got the package back in the software repo
but then lost it trying to install and then clean.


below is the standard way that did not work for 
1. Uninstall Gimp from your system:

sudo apt-get autoremove gimp gimp-plugin-registry

2. Add the following PPA:

sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update

3. Install Gimp:

sudo apt-get install gimp


It is a gamble to install new stuff. I want the single window gimp feature in this new version. I get crazy and excited about the software and need to refrain from these actions ;)

---

### Post by Warren North on 2012-09-28
I found a work around.
I went to portable apps and installed gimp that way.
So it is working in wine now.
No problems at this point. 
Thanks for the help again ):P

---

