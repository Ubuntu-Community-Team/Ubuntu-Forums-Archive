---
title: "How do I update all programs?"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by Darrin on 2005-11-04
I read somewhere that it is possible to update all programs at once? Is this true? if so how?

---

### Post by estel on 2005-11-04
Update?

When software updates are release, Ubuntu will tell you as soon as the new packages are added to the repositories. Therefore, you don't need to update them all at once because they're always at their most recent (as long as you install the new versions as they are released).

Ubuntu policy is not to release any new upgrades to a piece of software. i.e. the only new packages that will be released _ever_ into the Breezy repos will be bug fixes. Firefox 1.5 will not be released in there. 

Are you refering to a dist-upgrade where you can upgrade to the next release (Dapper Drake) which will always have the most recent features of software?

---

### Post by markr on 2005-11-04
sudo apt-get update
auso apt-get upgrade

I think that will ugrade all your packages to the latest available in the ubuntu repositories.

Mark.

ps.  The update will only refresh the lists held in your repositories list

---

### Post by Darrin on 2005-11-04
I was just wondering about application updates (Gimp,Gaim,Firefox, etc...) I wasnt sure If I would get notification of these updates if needed, or if I must manually go and check for updates for each application in my list.

---

### Post by Qrk on 2005-11-04
You don't have to do that. Everything you install via synaptic or apt-get (also the add/remove apps program) is supported by the update manager. Apt-get upgrade will aslo give the same effect. Gimp, firefox, gaim, Openoffice, etc included.

Its one of the high points of Ubuntu over Windows, and yet another thing that makes apt-get and debian wonderful.  

If you want to get upgrades to newer versions, (like firefox 1.5 or openoffice 2.0), you'll need to add backports. I don't think they are  up yet though. They will be when Dapper Drake gets a little more devolpment.

---

### Post by Darrin on 2005-11-04
Thanks good to know.

---

