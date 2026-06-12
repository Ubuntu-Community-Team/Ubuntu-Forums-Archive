---
title: "how to uninstall OSS-linux"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Pindulet on 2007-04-23
Is there a way to uninstall oss-linux manually. I seems like a failed instalation of oss is somehow blocking the whole system.
Everytime i try to install something or make other changes the terminal tells me: 

"the package needs to be reinstalled but I can't find any archive with it"

if I write: sudo apt-get remove oss-linux 

it does the same thing!!

thank you

---

### Post by aberry5555 on 2007-04-23
try "sudo apt-get ?" to get all the commands, I think there is one that says "reinstall" or something similar. Try that and then try uninstalling it afterward.

---

### Post by Pindulet on 2007-04-23
It didn't help because it just gives me this message again :confused: 

```
Reading package lists... Done
Building dependency tree... Done
E: The package oss-linux needs to be reinstalled, but I can't find an archive for it.
```

on almost all commands. It gives this output whenever I try to install any program

---

### Post by Pindulet on 2007-04-23
I couldn't find reinstall.. only update or upgrade but they gave the same output

---

### Post by ajgreeny on 2007-04-23
Have a look at *man apt-get* in a terminal which may help you sort this out.  It sounds as if the **-f** switch (fix) or the **--purge** option may be what you need, and then reinstall.  This assumes you can actually find the oss-linux package in the repos to reinstall it if you need to, because your apt-get has already told you that it can not find an archive for it.

---

### Post by nbilal on 2007-06-10
Hey guys! Head on over to [package manager failure]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_remove_jedit_when_Synaptic_package_manager_fails_after_install") to find out exactly how to deal with this prob.

I've got a Creative Labs X-Fi card too, and oss-linux wasn't able to finish the install...had my package manager locked up for days :(

The above link will give you a way to force a purge of the mangled oss-linux install:
"sudo dpkg --remove --force-depends --force-remove-reinstreq oss-linux"

Anyway, worked for me, hope it works for you :D

Peace!

---

