---
title: "force remove package (mldonkey continue)"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-03
I've installed the mldnokey.deb (converted from .rpm) and it didn't work
after that I installed mldonkey-gui and mldonkey-server packages with package manager on ubuntu
I've got an error on the mldonkey-server pack (error1 , no fourter info given to me).
so I've tried to complete remove thouse packages and I've got the same error on the same package...
how can I complete remove it so I can install it properly ?

---

### Post by catlett on 2006-07-03
You have to know the debs full name but if you do try removing it through the terminalk with dpkg . You can use r or p. r is for remove and p is for purge which gets rid of everything associated with it. So if for sake of argument your deb was mldnokey.deb, enter one of these in the terminal ```
sudo dpkg -r mldnokey.deb 
``````
sudo dpkg -p mldnokey.deb
``` Try them and see if there are any errors.

---

### Post by MaximB on 2006-07-03
I tried thouse too , but it didn't work
the package I want to remove is mldonkey-server
when I try :  sudo dpkg -r mldnokey-server
I get :dpkg - warning: ignoring request to remove mldnokey-server which isn't installed - but I know it's not removed competly , as I see this package in the packages manager (advenced)
when I try :  sudo dpkg -p mldnokey-server
I get : Package `mldnokey-server' is not available.

1.what I do from here ?
2.and why I do not see the first package I installed :mldonkey_2.7.6-2_i386.deb
and how can I uninstall it ?

---

### Post by catlett on 2006-07-03
I don't really know. It can get weird when there are different versions of the same thing installed or tried to be installed . Did you try to remove the original deb?
```
sudo dpkg -r mldonkey_2.7.6-2_i386.deb
``` What happens then?
Also I would try aptitude for removing the server one. ```
sudo aptitude remove mldonkey-server
``` Aptitude is good at taking care of dependencies. It may be worth a shot to run an update/upgrade with aptitude and see if it can sort out the different mldonkey packages. ```
sudo aptitude update
``` ```
sudo aptitude upgrade
``` Did you try uninstalling through synaptic package manager? You said you found it in an advanced search. Can you get to the l;istinmg and select it. Then select "mark for removal". ?

---

### Post by MaximB on 2006-07-03
I've done like you said but :
code: sudo dpkg -r mldonkey_2.7.6-2_i386.deb
answer: dpkg: status database area is locked by another process
code: sudo aptitude remove mldonkey-server
answer:E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
code:  sudo aptitude update
answer: E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? (then bunch of packages being updated , don't know how - I've updated them an hour ago and then I get : )
Fetched 8B in 41s (0B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache
code:  sudo aptitude upgrade
answer: E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

done

the first thing I tried is to "mark for removal" then "mark for complete removal" but to no avail.
I even took a look at the processors to see if somthing like mldonkey was running - but it wasn't.

what shell I do now...

---

### Post by catlett on 2006-07-03
Sorry for the wait. I was posting elsewhere. I forgot to mention. You can't have Synaptic Package Manger open when you use the the terminal to remove something. They both are accessing the same place and can't get the other one "out of there way" so to speak.
So close synaptic and try the dpkg -r first. Then close the terminal and try removing the servere from synaptic

---

### Post by MaximB on 2006-07-04
no man...it didn't work
it says that the process is running...but I can't find it running in the system monitor...where can I find it and close it then ?

---

### Post by Gobinath Elangovan on 2006-08-28
I got the same problem.To fix this problem pls  try this command
"sudo chmod -c 0755 /var/lib/dpkg/lock" .
I hope this will help who got the same problem

---

### Post by jazzworksweb on 2006-09-13
> **MAXDDARK said:**
> I've installed the mldnokey.deb (converted from .rpm) and it didn't work
after that I installed mldonkey-gui and mldonkey-server packages with package manager on ubuntu
I've got an error on the mldonkey-server pack (error1 , no fourter info given to me).
so I've tried to complete remove thouse packages and I've got the same error on the same package...
how can I complete remove it so I can install it properly ?

sudo dpkg --remove --force-remove-reinstreq mldonkey-server

---

### Post by beow on 2007-02-11
have similar problem, found the last command but it doesn't work:

```
$ dpkg -l | grep gmediaserver
ri  gmediaserver                               0.11.0-1

$sudo dpkg --remove --force-remove-reinstreq gmediaserver
(Reading database ... 136079 files and directories currently installed.)
Removing gmediaserver ...
Stopping gmediaserver: invoke-rc.d: initscript gmediaserver, action "stop" failed.
dpkg: error processing gmediaserver (--remove):
 subprocess pre-removal script returned error exit status 1
Starting gmediaserver: Errors were encountered while processing:
 gmediaserver

$ dpkg -l | grep gmedia
ri  gmediaserver                               0.11.0-1
```

Still there! There is no mediaserver running (if that should make any change). Isn't there a way to really force just the deletion of these files? The problem locks up the apt database.

---

### Post by beow on 2007-02-22
> **beow said:**
> have similar problem, found the last command but it doesn't work:

```
$ dpkg -l | grep gmediaserver
ri  gmediaserver                               0.11.0-1

$sudo dpkg --remove --force-remove-reinstreq gmediaserver
(Reading database ... 136079 files and directories currently installed.)
Removing gmediaserver ...
Stopping gmediaserver: invoke-rc.d: initscript gmediaserver, action "stop" failed.
dpkg: error processing gmediaserver (--remove):
 subprocess pre-removal script returned error exit status 1
Starting gmediaserver: Errors were encountered while processing:
 gmediaserver

$ dpkg -l | grep gmedia
ri  gmediaserver                               0.11.0-1
```

Still there! There is no mediaserver running (if that should make any change). Isn't there a way to really force just the deletion of these files? The problem locks up the apt database.
See [http://ubuntuforums.org/showthread.php?t=366977](http://ubuntuforums.org/showthread.php?t=366977) for solution.

---

