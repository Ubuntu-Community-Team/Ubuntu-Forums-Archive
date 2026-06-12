---
title: "Could not download all repository indexes after executing this comand"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by esthrim on 2007-09-03
Hi,  i just following steps to install wine from ([http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)) 

those steps are  :

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

and

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

after that when i open the update manager it show error

Could not download all repository indexes
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

So How's to fix this problem??

thank you so much.

---

### Post by Perfect Storm on 2007-09-03
You need to close synaptic and/or add/remove application first. You can only run one thing at the time of commands/synaptic etc. when accessing the sources.list

---

### Post by nowshining on 2007-09-03
actually you need to do the last step first and the first step last - :) that's what i found out in feisty..
 
so do
 
sudo wget [http://wine.budgetdedicated.com/apt/....d/feisty.list]("http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list") -O /etc/apt/sources.list.d/winehq.list
 
then
 
 
sudo wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

---

