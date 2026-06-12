---
title: "Problem installing packages"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by kellybean on 2007-05-02
Get this error for every package I try apt-get from terminal.  This one was for qsynaptics.  What am I missing or doing wrong? Thanks for any help.



Setting up gnunet (0.7.0e-4ubuntu1) ...
Migrating previous GNUnet data (gnunet-update)
May 02 19:32:16 `bind' failed for port 2087: Address already in use. Is gnunetd already running?
Aborted (core dumped)
dpkg: error processing gnunet (--configure):
 subprocess post-installation script returned error exit status 134
Setting up qsynaptics (0.22.0-6.1) ...

Errors were encountered while processing:
 gnunet
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jfinkels on 2007-05-02
> **kellybean said:**
> Get this error for every package I try apt-get from terminal.  This one was for qsynaptics.  What am I missing or doing wrong? Thanks for any help.



Setting up gnunet (0.7.0e-4ubuntu1) ...
Migrating previous GNUnet data (gnunet-update)
May 02 19:32:16 `bind' failed for port 2087: Address already in use. Is gnunetd already running?
Aborted (core dumped)
dpkg: error processing gnunet (--configure):
 subprocess post-installation script returned error exit status 134
Setting up qsynaptics (0.22.0-6.1) ...

Errors were encountered while processing:
 gnunet
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can you remove gnunet? Type the following in the terminal:```
sudo aptitude remove gnunet
```

If that doesn't work, try this:```
sudo apt-get -f install
```

If you still are having trouble, post the output of the first command :D

---

### Post by kellybean on 2007-05-03
I'm not sure if it fixed the problem


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  gnunet-gtk 
The following packages will be REMOVED:
  gnunet 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 2814kB will be freed.
The following packages have unmet dependencies:
  gnunet-gtk: Depends: gnunet (>= 0.7.0e) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
gnunet-gtk

Score is -301

Accept this solution? [Y/n/q/?] y
The following packages will be automatically REMOVED:
  gnunet-gtk 
The following packages will be REMOVED:
  gnunet gnunet-gtk 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 3580kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 193972 files and directories currently installed.)
Removing gnunet-gtk ...
Removing gnunet ...
Stopping GNUnet: No /usr/bin/gnunetd found running; none killed.
gnunetd.

---

### Post by jfinkels on 2007-05-03
You should be all set now. Type the following, and if you have any problems come back (you shouldn't :D ):```
sudo aptitude update && sudo aptitude upgrade
```

---

