---
title: "Yum doesn't work and Add/Remove Software Don't work"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by grabyourhosting on 2007-08-03
I get the following error trying to use yum.

Warning, could not load sqlite, falling back to pickle
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm
Traceback (most recent call last):
  File "/usr/bin/yum", line 27, in <module>
    yummain.main(sys.argv[1:])
  File "/usr/share/yum-cli/yummain.py", line 75, in main
    base.getOptionsConfig(args)
  File "/usr/share/yum-cli/cli.py", line 170, in getOptionsConfig
    self.doConfigSetup(fn=opts.conffile, root=root)
  File "/var/lib/python-support/python2.5/yum/__init__.py", line 82, in doConfigSetup
    self.conf = config.yumconf(configfile=fn, root=root)
  File "/var/lib/python-support/python2.5/yum/config.py", line 271, in __init__
    self.yumvar['releasever'] = self._getsysver()
  File "/var/lib/python-support/python2.5/yum/config.py", line 383, in _getsysver
    idx = ts.dbMatch('provides', self.getConfigOption('distroverpkg'))
TypeError: rpmdb open failed

and when you click a program in the Add/Remove software the 0 takes forever to finish. I have never had this problem before..... So, I doubt its a hardware problem unless it suddenly is?

---

### Post by Steveway on 2007-08-03
You know that Ubuntu doesn't use Yum?
We use APT, wich is far superior to Yum.
What do you want to do?

---

### Post by grabyourhosting on 2007-08-03
I just want to install for example gftp. Could you give me a command for that using APT?

---

### Post by nichipet on 2007-08-03
> **grabyourhosting said:**
> 
and when you click a program in the Add/Remove software the 0 takes forever to finish.

Can you give an example? I've found Add/Remove to be plenty fast enough, not lightning quick but more than adequate.

---

### Post by Steveway on 2007-08-03
That sould be:
$sudo apt-get install gftp
If it fails, copy-paste the output here.

---

### Post by grabyourhosting on 2007-08-03
> **nichipet said:**
> Can you give an example? I've found Add/Remove to be plenty fast enough, not lightning quick but more than adequate.

I clicked Add/Remove Programs then the hour glass appears after i click the check box to add the software and it takes forever to finish.

---

### Post by sailor2001 on 2007-08-03
gftp is in synaptics

---

### Post by grabyourhosting on 2007-08-03
> **Steveway said:**
> That sould be:
$sudo apt-get install gftp
If it fails, copy-paste the output here.

I do that but here is the output.

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I login root by putting the following command: su -

Whats the root pass anyways? i can't even login as root. Do you specify a root pass when you install ubuntu?

---

### Post by Steveway on 2007-08-03
You need to close Add/Remove or Synaptic before using that command.
And the root password is your user password.
We don't use su we use sudo!

---

### Post by grabyourhosting on 2007-08-03
> **Steveway said:**
> You need to close Add/Remove or Synaptic before using that command.
And the root password is your user password.
We don't use su we use sudo!

Whats the command for sudo?

---

### Post by Steveway on 2007-08-03
*sigh*
If you need rootaccess you put the command sudo right before your command.
For example:
$sudo apt-get install gftp
You see?
Just open a terminal and copy this command into it.

---

### Post by Rocket2DMn on 2007-08-03
Only one package manager can run at a time, hence the problem obtaining the lock.
```
sudo apt-get install *packagename*
```
sudo is for super-user-do which allows the following command to be run with root privileges.
```
man apt-get
``` for more info on apt-get and [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more info on sudo.

---

### Post by grabyourhosting on 2007-08-03
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

---

### Post by Rocket2DMn on 2007-08-03
You have to close out your other package managers before you can run that command.  Close Add/Remove and Synaptic Package Manager and maybe run 
```
sudo killall apt-get
``` then you can run the install command.  If it still gives you the error, try rebooting, maybe something got stuck running in the background that is holding the lock.
PS: yum is for fedora (previously fedora core)

EDIT: if it told you to run "dpkg --configure -a", do it, then run the apt-get stuff.
```
sudo dpkg --configure -a
```

---

### Post by r4ik on 2007-08-03
Please read,

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

Good luck !

---

### Post by grabyourhosting on 2007-08-03
Looks like I need to reinstall virtual box......

Edit: I reinstalled Virtual Box then of course I gftp installed just fine! Thank you for your help!

Also the add/remove programs doesn't hang either! Yes!!!

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gftp-common gftp-gtk gftp-text
The following NEW packages will be installed:
  gftp gftp-common gftp-gtk gftp-text
0 upgraded, 4 newly installed, 0 to remove and 29 not upgraded.
Need to get 524kB of archives.
After unpacking 3785kB of additional disk space will be used.
Do you want to continue [Y/n]? y
0% [Working]
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main gftp-common 2.0.18-16ubuntu2 [78.1kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main gftp-gtk 2.0.18-16ubuntu2 [277kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe gftp-text 2.0.18-16ubuntu2 [124kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe gftp 2.0.18-16ubuntu2 [45.8kB]
Fetched 524kB in 2s (203kB/s)    
Selecting previously deselected package gftp-common.
(Reading database ... 134462 files and directories currently installed.)
Unpacking gftp-common (from .../gftp-common_2.0.18-16ubuntu2_i386.deb) ...
Selecting previously deselected package gftp-gtk.
Unpacking gftp-gtk (from .../gftp-gtk_2.0.18-16ubuntu2_i386.deb) ...
Selecting previously deselected package gftp-text.
Unpacking gftp-text (from .../gftp-text_2.0.18-16ubuntu2_i386.deb) ...
Selecting previously deselected package gftp.
Unpacking gftp (from .../gftp_2.0.18-16ubuntu2_all.deb) ...
Setting up gftp-common (2.0.18-16ubuntu2) ...
Setting up gftp-gtk (2.0.18-16ubuntu2) ...

Setting up gftp-text (2.0.18-16ubuntu2) ...

Setting up gftp (2.0.18-16ubuntu2) ...

---

### Post by floke on 2007-08-03
sudo apt-get install common-sense

should do it

---

### Post by grabyourhosting on 2007-08-03
Well it works now. Everything works fine since I installed Virtual Box and the Add/Remove Programs part doesn't hang either.

---

