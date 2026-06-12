---
title: "Fresh install Gutsy - keep existing programs"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-10-12
The object is to fresh install Gutsy and then install all the programs used on the present setup. I need to check the process so that I do not discover my oversight at the wrong time ..

So to save the list of what is installed
dpkg --get-selections > installed_applications

But in order to save bandwidth later it is a good idea to save the saved deb files at
/var/cache/apt/archives

It is also a good idea to save the user home directory so that the individual program settings may also be saved.

The process to restore the software on the new system then is .....

First edit the installed_applications file to edit out anything Linux* and gnome* since these represent history which is not needed. But what else can be dropped? (perhaps OO)

Then ....

copy the deb files to the new /var/cache/apt/archives directory

sudo apt-get update
sudo dpkg --set-selections < installed_applications
sudo apt-get -u dselect-upgrade

and then copy the program settings files from the user home directory.

Is this more or less correct? Or does anyone have any other suggestions ....?

---

### Post by ItalOz on 2008-01-22
The tread is interesting
I propose an UP ;-) for this.
Is this the right way to do?

---

### Post by philinux on 2008-01-22
[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)

This was for feisty so I'm sure similar for gutsy.

I've got home on its own partition so a fresh install is a doddle. I just mark the /home partition as not to format.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

