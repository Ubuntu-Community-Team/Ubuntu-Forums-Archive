---
title: "Held broken packages- can't fix."
date: 2012-02-09
forum: Any Other OS
---

### Post by toastermm on 2012-02-09
Running Ubuntu (mint-katya), and I'm trying to update the program Rkward (to 0.5.7), I added the repository and re-ran update manager.

Rkward does not show up in update manager, but shows up in synaptic.  When I select it to upgrade now (and click apply), it tells me:

> Could not apply changes!
Fix broken packages first.

So I clicked on "Fix broken packages" under the edit menu and get the message:

> E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

Not sure what that means, but I ran across a few threads with similar errors and what fixed their problem was running the commands:

> 
Me@Computer ~ $ sudo apt-get install -f
[sudo] password for Me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Me@Computer ~ $ sudo dpkg --configure -a
Me@Computer ~ $ sudo apt-get clean
Me@Computer ~ $ sudo apt-get update
...
[Long list of packages checked...]
...
Fetched 48.1 kB in 8s (5,436 B/s)
Reading package lists... Done


Then I ran into the same problem in synaptic.  This did not fix the problem.

Any ideas what I can do next?  Is there any other output I should give?

---

### Post by toastermm on 2012-02-09
From the terminal:

> 

Me@Computer ~ $ sudo apt-get install rkward
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 rkward : Depends: kde-runtime but it is not installable
E: Broken packages
Me@Computer ~ $ sudo apt-get install kde-runtime
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kde-runtime is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'kde-runtime' has no installation candidate



It would appear that rkward requires kde-runtime, but I can not install that.  This is strange to me as my home computer has rkward up and running.  Any suggestions?

---

### Post by toastermm on 2012-02-09
Fixed.

Went here:
[http://maketecheasier.com/install-kde-4-5/2010/08/18](http://maketecheasier.com/install-kde-4-5/2010/08/18)

Added the repository for KDE 4.5.

Reloaded synaptic, selected kde-runtime. Installed.

Installed Rkward- no problems.

Whew.:guitar:

---

