---
title: "Update Manager Errors"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Louwe Louwe on 2007-05-30
Goodness, I could use some help.

I installed Feisty Desktop from CD.  Then I attempted to install UbuntuStudio using the sudo / wget process.

Now when I run Update Manager, after the updates download, here is the error I get:

E: /var/cache/apt/archives/python2.5_2.5.1-0ubuntu1_i386.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/python2.5-minimal_2.5.1-0ubuntu1_i386.deb: subprocess dpkg-deb --control returned error exit status 2

Can anyone tell me what I'm doing wrong?

THanks!

---

### Post by dbbolton on 2007-05-30
i had a similar problem with Timidity. i uninstalled the programs that depended on timidity, reinstalled timidity, then did "mark all upgrades" and "apply" in synaptic.

---

### Post by Louwe Louwe on 2007-05-31
OK, so if I understand correctly, the update manager is trying to install several packages, but some of those packages depend on others being installed first?  In other words, there are 42 updates, update manager is installing them in alphabetical order, but they need to be installed in order of dependency?

So how do I find out which package needs to come first, second, etc.?

Thanks again.

---

### Post by dbbolton on 2007-05-31
> **Louwe Louwe said:**
> OK, so if I understand correctly, the update manager is trying to install several packages, but some of those packages depend on others being installed first?  In other words, there are 42 updates, update manager is installing them in alphabetical order, but they need to be installed in order of dependency?

So how do I find out which package needs to come first, second, etc.?

Thanks again.
no, it's just that somehow your python package is broken. go to System > Administration > Synaptic Package Manager, then click on Search, and search "python2.5".  you should end up seeing a package marked "python2.5" and "python2.5-minimal". click on the box beside these two packages and choose Mark for Reinstallation, then click Apply.

if that works, then click Mark All Upgrades (at the top) then Apply.

---

### Post by woohhaa on 2007-07-06
I was having the same python2.5 error after running the update manager than your method fixed it dbbolton. Thanks!

---

