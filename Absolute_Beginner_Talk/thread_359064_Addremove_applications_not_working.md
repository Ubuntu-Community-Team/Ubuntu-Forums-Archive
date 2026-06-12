---
title: "Add/remove applications not working"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by hanbaked on 2007-02-11
Hello

Can anyone let me know what may be causing the following problem:

In Add/remove applications, after the checking and installing available applications message, the next message is: The list of available applications is out of date. The action required is to reload. I press the reload button, put in my password but the downloading package information gets stuck on file 7 out of 28. When I click 'show progress of single files' it shows the status of most as failed.

If I go into the terminal and ping, the downloading package information then gets stuck on 36 out of 45.

My questions are a) what's happening? and b) is the problem to do with the security in the network router?

Thanks

---

### Post by taurus on 2007-02-11
Try to run these two commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by hanbaked on 2007-02-11
I typed in the first command, pressed enter and was asked for my password.  I gave that, typed enter and the following text appeared:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Translation-en_GB
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Translation-en_GB
20% [Connecting to uk.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubun

Could you let me know what should I do now?

Thanks

---

### Post by taurus on 2007-02-11
Try

```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by hanbaked on 2007-02-11
This is the message:

hannah@ubuntu:~$ sudo dpkg --configure -a
Password:
Setting up synaptic (0.57.11ubuntu12.1) ...
sudo aptitude update
sudo aptitude upgrade
dpkg: error processing synaptic (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Setting up ubuntu-docs (6.10.4.1) ...
dpkg: error processing ubuntu-docs (--configure):
 subprocess post-installation script killed by signal (Interrupt)
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 synaptic
 ubuntu-docs
 update-manager
 update-notifier
hannah@ubuntu:~$ sudo dpkg --configure -a
Setting up synaptic (0.57.11ubuntu12.1) ...
sudo aptitude update
sudo aptitude upgrade

Setting up ubuntu-docs (6.10.4.1) ...

Setting up update-manager (0.45.1) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 480 strings at 20 - 27dc
Wrote aliases at 27dc - 2990
Wrote parents at 2990 - 3360
Wrote literal globs at 3360 - 33c4
Wrote suffix globs at 33c4 - 674c
Wrote full globs at 674c - 6770
Wrote magic at 6770 - bd80
Wrote namespace list at bd80 - bd90
***

Setting up update-notifier (0.43.3) ...

hannah@ubuntu:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Translation-en_GB
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Translation-en_GB
Err [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg                    
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg                         
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) edgy Release.gpg                               
  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                        
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_GB         
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_GB        
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) edgy/main Translation-en_GB                    
  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_GB             
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_GB              
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) edgy/restricted Translation-en_GB              
  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_GB       
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_GB        
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) edgy/universe Translation-en_GB                
  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_GB         
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_GB          
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) edgy/multiverse Translation-en_GB              
  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_GB       
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) edgy-updates Release.gpg
  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) edgy-updates/main Translation-en_GB
  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) edgy-updates/restricted Translation-en_GB
  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) edgy-updates/universe Translation-en_GB
  Could not connect to uk.archive.ubuntu.com:80 (1.0.0.0), connection timed out
20% [Connecting to uk.archive.ubuntu.com (1.0.0.0)]

---

### Post by hanbaked on 2007-02-11
Apologies - I was a bit quick off the draw and it hadn't finished.  This is the follow up:

Reading package lists... Done                      
hannah@ubuntu:~$ sudo aptitude upgradesudo aptitude update
Password:
Unknown command "upgradesudo"
aptitude 0.4.1
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
 remove       - Remove packages
 purge        - Remove packages and their configuration files
 hold         - Place packages on hold
 unhold       - Cancel a hold command for a package
 markauto     - Mark packages as having been automatically installed
 unmarkauto   - Mark packages as having been manually installed
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages
 upgrade      - Perform a safe upgrade
 dist-upgrade - Perform an upgrade, possibly installing and removing packages
 forget-new   - Forget what packages are "new"
 search       - Search for a package by name and/or expression
 show         - Display detailed information about a package
 clean        - Erase downloaded package files
 autoclean    - Erase old downloaded package files
 changelog    - View a package's changelog
 download     - Download the .deb file for a package
 reinstall    - Download and (possibly) reinstall a currently installed package

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z                 Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends Specify whether or not to treat recommends as
                strong dependencies
 -S fname: Read the aptitude extended status info from fname.
 -u      : Download new package lists on startup.
 -i      : Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.
hannah@ubuntu:~$ 

What does this mean?  Is the problem solved?

Thank you

---

### Post by citizenofnowhere on 2007-03-09
I ran into the exact same problem after running an upgrade the other day. Here is the output of my 
```
sudo dpkg --configure -a
```

```

Setting up gnome-applets (2.16.1-0ubuntu4) ...
Compiling /usr/lib/python2.4/site-packages/livewires/games.py ...
  File "/usr/lib/python2.4/site-packages/livewires/games.py", line 1739
    % (self.xpos(), self.ypos(), ["filled","unfilled"][not self._filled],
    ^
SyntaxError: invalid syntax

dpkg: error processing gnome-applets (--configure):
 subprocess post-installation script returned error exit status 1
Setting up update-manager (0.45.1) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 483 strings at 20 - 2830
Wrote aliases at 2830 - 29e4
Wrote parents at 29e4 - 33c8
Wrote literal globs at 33c8 - 342c
Wrote suffix globs at 342c - 68e4
Wrote full globs at 68e4 - 6908
Wrote magic at 6908 - c008
Wrote namespace list at c008 - c018
***
Compiling /usr/lib/python2.4/site-packages/livewires/games.py ...
  File "/usr/lib/python2.4/site-packages/livewires/games.py", line 1739
    % (self.xpos(), self.ypos(), ["filled","unfilled"][not self._filled],
    ^
SyntaxError: invalid syntax

dpkg: error processing update-manager (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager; however:
  Package update-manager is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-applets
 update-manager
 update-notifier

```

I've tried removing and reinstalling the packages. I've tried downgrading to the version I had before - nothing helps. I'd really appreciate any thoughts

---

### Post by citizenofnowhere on 2007-03-09
I managed to fix my problem, and now I'm not sure if it's related to this thread but I'll put up what I did anyway it case it does help.

My problem was that livewires wasn't compiled correctly. Livewires is a package that helps beginners learn Python, but I think it must have been written for an older Python version. So I edited my  /usr/share/python/debian_defaults file to look like this:

```

[DEFAULT]

# the default python version
default-version = python2.4

# all supported python versions
supported-versions = python2.4, python2.5

# formerly supported python versions
#old-versions = python2.3

```

After that I ran the livewires setup script as root (not sudo) and the the rest of the installation went without errors. I was then able to reinstall the packages that gave me problems.

---

