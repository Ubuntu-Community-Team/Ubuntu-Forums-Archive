---
title: "Trying to install WINE, minor problems"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by JZeFF on 2007-07-16
Ok, let me start by saying i have never even seen the linux desktop b4 today.  I installed ubuntu 7.04 today on my other hard drive, and i was reading on how to install wine, thats where the confusion starts..

From what i read i need to....

Add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -


To add repositories i read that i needed to do   system/administration/software sources.      PROBLEM # 1    software sources was not there.    So i right clicked on the bar at the top and hit customize, got a new window that gave me options of what to put under the administration thing,    and sure enough    Software sources was unchecked, so i checked it,   and after about 1.5 seconds it unchecked itself.     what is going on here? 

Trust me, i will have more questions,   but this is just the first.

---

### Post by uways on 2007-07-16
can't you just use the ubuntu repositories instead?

---

### Post by JZeFF on 2007-07-16
I use windows thats it, this is my first time using anything else,   

What do u mean by using the ubuntu repositories????

Im pretty sure its not recognizing me as an admin also, because wheni try to run a system update and i enter my password it gives me some error message, any ideas on that one?  I know my password is correct

I got this when it asked me to enter my password when i tried to run the update manager 

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '41943043' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpy2Sq2V' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

It said there was 90 updates....

---

