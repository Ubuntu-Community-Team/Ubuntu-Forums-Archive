---
title: "BUM will not allow deselection of LVM or RAID from run level S"
date: 2005-10-03
forum: BUM - Boot Up Manager
---

### Post by azteech on 2005-10-03
Hello,

Fairly new to the forum, as well as to ubuntu. I have 5.10 (breezy) installed on my computer.

Recently downloaded and installed BUM. When trying to deactivate certain scripts for raid and LVM, I get the message

"Editing in run level S is not allowed! Playing with rcS.d symlinks is an administration activity requiring deep knowledge of the runlevel system."

I do not need Raid, or LVM running and I am not able to stop the scripts from run level S. 

Is there a way to have BUM run administrative functions with only SUDO administrative options available? Or are there other options I need to consider to shut down/disable certain scripts?

---

### Post by mlomker on 2005-10-03
> Or are there other options I need to consider to shut down/disable certain scripts?

That looks like a nice tool but it isn't the only way to disable scripts.

**update-rc.d -f *servicename* remove**

---

### Post by Akoluth of Nandus on 2005-10-05
[QUOTE=mlomker]That looks like a nice tool but it isn't the only way to disable scripts.
**update-rc.d -f *servicename* remove**[/QUOTE]
The fine thing with BUM is that it stores the sequence code of a removed service. Thus the startup sequence doesn't get screwed up if you reenable the service at sometime later and don't remember at which position it was.
*update-rc.d* adds the service at S20 if you don't specify another number.

---

### Post by action09 on 2005-11-05
Hi,

It's a french link but it's the same that explained above :)
[http://www.xhtml.net/breves/170-Optimiser-Le-Demarrage-Dubuntu-Linux](http://www.xhtml.net/breves/170-Optimiser-Le-Demarrage-Dubuntu-Linux)

---

### Post by dagnabit dang doohickey on 2006-10-25
> **azteech said:**
> Hello,
Recently downloaded and installed BUM. When trying to deactivate certain scripts for raid and LVM, I get the message

"Editing in run level S is not allowed! Playing with rcS.d symlinks is an administration activity requiring deep knowledge of the runlevel system."

I do not need Raid, or LVM running and I am not able to stop the scripts from run level S. 

Is there a way to have BUM run administrative functions with only SUDO administrative options available? Or are there other options I need to consider to shut down/disable certain scripts?

When trimming down my startup, I also wanted to stop lvm (and evms and mdadm as well), so instead of messing with the symlinks (which I initially started doing), I used synaptic to completely remove the following packages. *Be sure you don't need them before removal.*

lvm-common
lvm2
evms
evms-ncurses
libevms-2.5
mdadm
(these meta packages will also be removed: ubuntu-base ubuntu-standard)

While I was at it, I also removed the festival and britty packages since I didn't need those either.

---

