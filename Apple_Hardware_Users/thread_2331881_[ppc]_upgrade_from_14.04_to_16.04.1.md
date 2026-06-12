---
title: "[ppc] upgrade from 14.04 to 16.04.1"
date: 2016-07-26
forum: Apple Hardware Users
---

### Post by sacarde on 2016-07-26
hi,
   in my Mini ppc G4 I have lubuntu-14.04
if I try to upgrade with:

```
do-release-upgrade
```

I have: No new release found


why? 



thank you

---

### Post by PaulW2U on 2016-07-26
See [No notification for 16.04.01 LTS]("https://ubuntuforums.org/showthread.php?t=2331436").

I haven't seen anything that confirms the notification has now been enabled. I could be wrong of course but in any case the intention was for the notification to be enabled sometime this week.

---

### Post by ajgreeny on 2016-07-26
I understand that there is currently a bug in the upgrade process to 16.04.1  which is being sorted out and the process was thus withdrawn until such time as it works as expected.

Watch this space.

---

### Post by sacarde on 2016-07-26
here [http://lubuntu.me/downloads/](http://lubuntu.me/downloads/) I read:

> 
We did NOT release a 16.04.1 LTS image for PowerPC, but you can download the 16.04 LTS image below


what does it mean ?

---

### Post by PaulW2U on 2016-07-26
It means that for those installing Lubuntu from a downloaded PowerPC image they will be using the slightly older 16.04 release rather than latest 16.04.1. I understand there was a shortage of testers so it was thought that it was best to not release an untested image.

That won't affect online upgrades though which automatically upgrade all packages to the latest version currently in the repositories.

---

### Post by sacarde on 2016-07-26
what do you suggest:

1. wait
2. do-release-upgrade -d
3. do-release-upgrade -p
?

---

### Post by PaulW2U on 2016-07-28
> **sacarde said:**
> what do you suggest:
Sorry I didn't get back to you earlier sacarde but I was away from my PC most of yesterday. 

It's your PC or laptop so it's your decision on which option to make. If 14.04 is working for you then why worry about upgrading? The Release Team must have their reasons for delaying the upgrade notification so may be you should **wait**.

howefield's [post]("https://ubuntuforums.org/showthread.php?t=2331971&p=13523299&viewfull=1#post13523299") implies that what you are waiting for is imminent but today is not only **End of life** for Wily but the **release** day for Yakkety Alpha 2.

There's a lot happening for the Release Team this week.

---

### Post by sacarde on 2016-07-28
thanks  PaulW2U !


but if I run:  "do-release-upgrade -d"

it upgrade to 16.04.1 ? not?

---

### Post by sacarde on 2016-07-31
this morning "do-release-upgrade" have found xenial.tar.gz

now it is my doubt:

to upgrade or not to upgrade !

---

### Post by sacarde on 2016-08-04
I upgrade to 16.04

all OK except some PAM* packages and some servers adjustments (from upstart to systemd)


thanks

---

