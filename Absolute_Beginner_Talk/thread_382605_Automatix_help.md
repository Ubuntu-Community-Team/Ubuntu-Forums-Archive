---
title: "Automatix help"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by john38242 on 2007-03-12
I tried to install automatix everything seems to work fine intill the last part and this what I get 

The following packages have unmet dependencies:
  automatix2: Depends: tango-icon-theme-extras but it is not installable
E: Broken packages

I went to the package manger and searched for Tango it says its installed so what should I do

---

### Post by astrolabio on 2007-03-12
have you tried
sudo apt-get install tango-icon-theme-extras

if it doesn't work you may need to update your sources.list file.
You have to do that to activate many repository not included by default mostly for licensing issues.

You can activate them using synaptic or with the old school way:

gksu "gedit /etc/apt/sources.list"

and decommenting the repositories .

For example when you find something like
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

you take out  the # and make it
 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

You do that for avery deb or deb-src line. Not for the lines that starts with a double ##. You leave the ## lines alone :)

Save the file and update
sudo apt-get update
And finally you should be able to install your file
sudo apt-get install tango-icon-theme-extras

---

