---
title: "upgrade kind of worked"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-09-26
last night i upgraded my distrubution to 7.04 and this morning i turned it on and the splash screen just hung there, i used the grub loader to boot from a different kernel version and booterd from the oldest one still installed on my computer[also known as the one that was installed with 6.10] the two that are most recent appear to be fried, the most recent seems to just hang[i left the comp on for a feww ours wen i fell asleep again] and the other isnt much different. the reason i am posting this is i wish to know how to fix this
the kernel versions on my computer are  2.6.17-10-generic, 2.6.17-12-generic, 2.6.20-15-386, 2.6.20-16-generic, 2.6.20-16, 2.6.20.16-generic
what do i have to do to fix the problem?
should i reinstall them?
and if so which ones?
or do i uninstall any of them?

---

### Post by 99bluefoxx on 2007-09-26
any ideas at all? anyone?anything?
i would like some ideas before i do anything as i do not wish to ruin my system.

---

### Post by ThrobbingBrain66 on 2007-09-26
when you're booted with the old kernel, go into your menu.lst
```
gksudo gedit /boot/grub/menu.lst
```
and take the 'quiet' option off of the misbehaving kernel.

You will now see a scrolling list as it boots up and you'll be able to see what step is stalling the boot.

---

### Post by 99bluefoxx on 2007-09-26
> **ThrobbingBrain66 said:**
> when you're booted with the old kernel, go into your menu.lst
```
gksudo gedit /boot/grub/menu.lst
```
and take the 'quiet' option off of the misbehaving kernel.

You will now see a scrolling list as it boots up and you'll be able to see what step is stalling the boot.
```
 bluefoxx@azurE-prIDE:~$ gksudo gedit /boot/grub/menu.lst
(gedit:21719): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
bluefoxx@azurE-prIDE:~$ 


```

---

### Post by rsambuca on 2007-09-26
At the grub menu, just select a kernel that isn't working and press 'e' to edit the line.  Go to the end of the kernel line and delete the words 'quiet' and 'splash'. Then boot up and see where it is hanging.

---

### Post by 99bluefoxx on 2007-09-26
ok gonna try that now
thanks

---

### Post by 99bluefoxx on 2007-09-26
ok 
afr checking all kernels that i have i have found that the two that dont work are 2.6.17-12generic and 2.6.20-16-generic, both stalling at "waiting for root file system"
now what?
and thanks for help so far^^

---

### Post by 99bluefoxx on 2007-09-27
any suggestions?
should i disable these kernels or reinstall them or uninstall them or what?

---

### Post by 99bluefoxx on 2007-09-27
please?help?anyone?anything?

---

