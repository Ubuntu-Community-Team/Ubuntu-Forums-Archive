---
title: "Ubuntu 6.06 Will not install on G4 and ibook"
date: 2006-06-07
forum: Apple PPC Users
---

### Post by dmoore7 on 2006-06-07
I have the latest version of Ubuntu and cannot get it to install on either of my mac's. I have a PowerMac G4 dual processor with 2 hard drives and when the boot from cd process starts I get several of these errors:
**Buffer I/O error on device hde, logical block**

For my ibook G4 I get to the spash screen and then it just goes black, I tried the novid option and that didn't help

I'm very new to Ubuntu but was able to get it installed on one my Dell computers in the i386 format, I would like to have 2 clean installs on both of my mac's as well, I'm not looking to have a dual boot system.

---

### Post by n00bWillingToLearn on 2006-06-07
Have you tried the text based installer?
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-powerpc.iso](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-powerpc.iso)

It is arguably harder to use / easier to mess up, but if you really don't want a dual boot, and you don't have any importand data on the computer at the moment, then what is there to loose?:)

---

### Post by godard on 2006-06-08
This might also be partially to do with this bug which has clobbered a lot of us with G4's [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508)

---

### Post by dmoore7 on 2006-06-08
[QUOTE=n00bWillingToLearn]Have you tried the text based installer?
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-powerpc.iso](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-powerpc.iso)

It is arguably harder to use / easier to mess up, but if you really don't want a dual boot, and you don't have any importand data on the computer at the moment, then what is there to loose?:)[/QUOTE]


I'm very new to Ubuntu what about a non-dual boot would make it harder to use? I think the problem with my install is the kernel for the G4, for both of my mac's I was able to get all the way through the install up until the part where it installs the linux kernel, at that point the installation fails. Thanks for the link to the text based installer, that got me a lot further than the Live CD.

---

### Post by dmoore7 on 2006-06-08
[QUOTE=godard]This might also be partially to do with this bug which has clobbered a lot of us with G4's [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508)[/QUOTE]


This has to be the problem, thanks for the input, is there a work around or any mention of when a patch to resolve this installation issue will be released?

---

### Post by n00bWillingToLearn on 2006-06-08
[QUOTE=dmoore7]I'm very new to Ubuntu what about a non-dual boot would make it harder to use? I think the problem with my install is the kernel for the G4, for both of my mac's I was able to get all the way through the install up until the part where it installs the linux kernel, at that point the installation fails. Thanks for the link to the text based installer, that got me a lot further than the Live CD.[/QUOTE]

Sorry, I meant that the text based installer was harder and that not having a dual boot was easier because you don't have to worry about wiping out OS x if you screw up the install. Since you don't have to worry about loosing OS x there is no risk in expirementing with the text based installer. I hope that makes sense.

---

### Post by dmoore7 on 2006-06-08
[QUOTE=n00bWillingToLearn]Sorry, I meant that the text based installer was harder and that not having a dual boot was easier because you don't have to worry about wiping out OS x if you screw up the install. Since you don't have to worry about loosing OS x there is no risk in expirementing with the text based installer. I hope that makes sense.[/QUOTE]


That makes perfect sense, thanks again for the reply.

---

