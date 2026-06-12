---
title: "How to Fix corrupt kdm package"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Robbi_az on 2006-10-19
Heya, 

I just installed a fresh copy of Dapper with KDE! But am having trouble as below...

robbi@Robbi:~$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  amarok: Depends: amarok-xine but it is not going to be installed
          Depends: ruby but it is not going to be installed
          Depends: python-qt3 but it is not going to be installed
          Depends: libifp4 but it is not going to be installed
          Depends: libtunepimp3 (>= 0.4.2) but it is not going to be installed
          Depends: libvisual-0.4-0 (>= 0.4.0) but it is not going to be installed
  kdm: Depends: kdebase-bin (= 4:3.5.2-0ubuntu27) but 4:3.5.3-0ubuntu0.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

--------------------------------------------------

So, i thoguht why not... and gave it a go...

--------------------------------------------------


robbi@Robbi:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  kdm
0 upgraded, 0 newly installed, 1 to remove and 20 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1503kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing kdm (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
robbi@Robbi:~$ Errors were encountered while processing:
 kdm

Can anyone give me any clues on what i need to do to fix the package... so that i can continue downloading/instlaling other packages ?

Thanks, Rob

---

### Post by Robbi_az on 2006-10-19
oh forgot to mention... tired going in to synaptic and marking for reinstallation.... and i got the following...

E: Unable to correct problems, you have held broken packages.
E: Unable to lock the download directory

Then tried marking it for removal.. thyinking i could jsut reinstall afterwards, but i got the following...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

... which of course i have already tried !

Any ideas anyone ?

---

### Post by Robbi_az on 2006-10-19
When i tried it... 

robbi@Robbi:~$ sudo dpkg --configure -a
robbi@Robbi:~$

.. seems to have done absolutely nothing... !

---

