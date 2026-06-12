---
title: "No Longer Able To Update"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by WPAStrangla on 2006-09-28
Im running the new Edgy beta, Everything was running great, got everything installed. But then when I went to update I get the errors below.

---

### Post by ewl1217 on 2006-09-28
Sorry, but those screenshots are too small. Could you post larger ones or copy and paste the error message(s) here?

Also, could you post your sources.list?

---

### Post by WPAStrangla on 2006-09-28
The First Screenshot Says:
> 
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

After following its instructions

The Second Screenshot in the Terminal says:

> shawn@shawn-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

---

### Post by ewl1217 on 2006-09-28
Are you using any third-party repositories or packages. These may sometimes cause ugly package conflicts. From what I know, I can't imagine what else went wrong. It might, unfortunately, be an issue with Edgy that hasn't been worked out yet. Just remember that Edgy is a beta and nothing more right now.

---

