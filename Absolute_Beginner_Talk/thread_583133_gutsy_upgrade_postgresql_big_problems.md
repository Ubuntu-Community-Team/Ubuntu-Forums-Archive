---
title: "gutsy upgrade postgresql big problems"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by randomjohn on 2007-10-20
I did upgrade manager when it told me gutsy was available and left it unattended while it downloaded everything.  it rebooted and everything seemed to have progressed normally.  I then went to run it again to make sure everything else was updated.  I get the following error:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

so I do the terminal command and get the following

```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  postgresql-client-8.2 postgresql-client-common postgresql-common postgresql-8.2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  postgresql-8.2 postgresql-client-8.2 postgresql-client-common postgresql-common
Suggested packages:
  oidentd ident-server postgresql-doc-8.2
The following NEW packages will be installed:
  postgresql-client-8.2 postgresql-client-common postgresql-common
The following packages will be upgraded:
  postgresql-8.2
1 upgraded, 3 newly installed, 0 to remove and 1063 not upgraded.
1 not fully installed or removed.
Need to get 0B/4216kB of archives.
After unpacking 877kB disk space will be freed.
Do you want to continue [Y/n]?

```I've tried answering both ways, but for purposes of this post, I'll show what happens when I answer no...

I do sudo apt-get autoremove

and get
```

sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  postgresql-8.2: Depends: postgresql-client-8.2 but it is not installed
                  Depends: postgresql-common (>= 63) but it is not installed
E: Unmet dependencies. Try using -f.
```so I try it with the switch

```
sudo apt-get autoremove -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  postgresql-client-8.2 postgresql-client-common postgresql-common postgresql-8.2
The following packages will be REMOVED:
  postgresql-8.2
0 upgraded, 0 newly installed, 1 to remove and 1063 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 17.9MB disk space will be freed.
Do you want to continue [Y/n]?
dpkg: error processing postgresql-8.2 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 postgresql-8.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```...and so on.  I just can't get rid of, reinstall or upgrade postgresql-8.2

Any suggestions?

---

### Post by Pumalite on 2007-10-20
Try:

sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by randomjohn on 2007-10-20
No dice...

```
sudo dpkg --remove --force-remove-reinstreq postgresql-8.2
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 146222 files and directories currently installed.)
Removing postgresql-8.2 ...
.: 19: Can't open /usr/share/postgresql-common/maintscripts-functions
dpkg: error processing postgresql-8.2 (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 postgresql-8.2

```

but at least it looks like a different error

---

### Post by Pumalite on 2007-10-20
How about this:

sudo apt-get remove --purge <packagename>

---

### Post by randomjohn on 2007-10-20
For no particular reason I went back into synaptic and tried repairing the broken package.  This hadn't worked before, but something changed and it worked this time.  It's now applying all the updates.  Thanks for the help.  I don't know what fixed it, but it looks like I'm making a little more progress now.

---

### Post by Pumalite on 2007-10-20
Good luck.

---

