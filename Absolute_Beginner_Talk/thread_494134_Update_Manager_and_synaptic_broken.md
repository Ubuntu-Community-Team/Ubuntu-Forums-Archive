---
title: "Update Manager and synaptic broken"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by mc4100 on 2007-07-06
Hey, can anyone help?

Last thing i did was try to install 'gparted' through synaptic, but it crashed during installation. When i try to open synaptic again i get:


E: Problem parsing dependency Depends
E: Error occurred while processing librsvg2-common (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

same sort of thing for the update-manager

any ideas how to fix it?

---

### Post by shrift on 2007-07-06
Have you tried doing "sudo aptitude update"?

---

### Post by locke.dragon on 2007-07-17
usually gparted is included in ubuntu.  and in my experience, i've found that when something like this happens, the best thing to do is just start over by re-installing.  back up your data (or make a separate home partition) and re-install.  it's WAY easier than trying to sort out the major problem.

---

