---
title: "Problem installing 915resolution"
date: 2006-07-22
forum: Apple PPC Users
---

### Post by Christiaan on 2006-07-22
I run 'apt-get install 915resolution' and get this:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

When I run 'sudo apt-get install 915resolution' I get this:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package 915resolution

Am I doing something wrong?

---

### Post by chasisaac on 2006-07-23
> **Christiaan said:**
> I run 'apt-get install 915resolution' and get this:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

When I run 'sudo apt-get install 915resolution' I get this:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package 915resolution

Am I doing something wrong?


You need to link the correct repositories 

The easy way to do this. 
System -> Adminstratian -> Synaptic Package Manager

Inside SPM 
Systems -> Repositories

CLick all the binary ones on (okay maybe not all) I am not to sure where it is located. 

Save.
Reload
Reinstall.

---

### Post by Christiaan on 2006-07-24
Thanks, that did the trick.It was actually: Settings > Repositories

Seems strange that this is not on by default?

---

### Post by hajk on 2006-07-24
You are -- judging from another post -- running Ubuntu in a Parallels virtual machine (VM) on an Intel-based Mac. It is important that you mention this in your posts, since most people visiting this forum install Ubuntu directly to the HD (with BootCamp or rEfit), so might be forgiven to answer your questions on that assumption.

Just to be clear about this: the Parallels VM is based on an Intel i810 PC (all in software), whereas a direct install to an Intel-based Mac deals directly with the hardware.

That shouldn't keep you from sharing any questions or experience with us (I'm about to try Parallels myself any day now...). :-D

---

### Post by Christiaan on 2006-07-24
Thanks, sorry 'bout that.

---

### Post by hajk on 2006-07-24
No harm done...

---

