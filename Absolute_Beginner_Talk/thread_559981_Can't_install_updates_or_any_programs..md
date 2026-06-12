---
title: "Can't install updates or any programs."
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by hung0702 on 2007-09-25
Initially, I could install all the updates. Then, I guess I messed something up when trying to install vmware or envy or any other of a slew of unsuccessful installs, and now I can't install any updates or any programs.

This is what I get when I try to install updates after downloading them:
[PHP]Not all changes and updates succeeded. For further details of the the failure, please expand the 'terminal' panel below.[/PHP] (it actually has double "the's")

Then the panel says:
[PHP]dpkg: parse error, in file `/var/lib/dpkg/available" near line 2 package libberylsettings0':
 value for `status' fields not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error case (2)
A package failed to install.  Trying to recover:[/PHP]

Does anyone know what I should do? Also, I changed my user to the root group because I thought that was the problem. But it didn't help, so should I change it back?

---

### Post by Clay_Banger on 2007-09-25
first, change your user back from the root group to the one it was in before.

it looks like beryl could be the problem, so in synaptic remove anything that is installed with beryl in it, and try updating/installing again.

---

### Post by Pumalite on 2007-09-25
[https://answers.launchpad.net/ubuntu/+question/10265](https://answers.launchpad.net/ubuntu/+question/10265)

[http://ubuntuforums.org/showthread.php?p=3317509#post3317509](http://ubuntuforums.org/showthread.php?p=3317509#post3317509)

---

### Post by hung0702 on 2007-09-26
Thanks to both of you. I'm not sure which one did it, perhaps the second one since it was tested out before, but it fixed the problem.

---

