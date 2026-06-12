---
title: "New to Ubuntu Help please"
date: 2008-04-24
forum: Apple Hardware Users
---

### Post by dlabutte on 2008-04-24
I have installed Ubuntu 6.10 on my powerpc64. No other versions would install right. Now that it is installed I get loud fan noise which is really annoying.
Is there a newer version of Ubuntu that I can use?
Does anyone know how to stop the fan noise?

---

### Post by slacka-vt on 2008-04-24
> I have installed Ubuntu 6.10 on my powerpc64. No other versions would install right. Now that it is installed I get loud fan noise which is really annoying.
Is there a newer version of Ubuntu that I can use?
Does anyone know how to stop the fan noise?

Well my friend, you've come to the right place at the right time.
That fan problem you have on Ubuntu 6.06 "Dapper Drake" is due to the fact that
the kernel that comes installed with that version has no "thermal control" (fan control)

I agree with you completely that "Dapper" is/was the only version of Ubuntu that would install "properly" as it was "properly" supported for the PPC architecture.

The good news is that Ubuntu 8.04 "Hardy Heron" has just been officially released today !

Though there is no "official" PPC support, there is a PPC installer for your machine.

However, I have some bad news for you. 

I would be losing the respect of my comrades here on the Ubuntu Forum if I did not flame you repeatedly for not conducting a proper "search" of the forums to find the answers you have requested. There are an almost infinite amount of references to your issue.

Apparently, I am also not "allowed" to tell you where the PPC Ubuntu Hardy Install ISO images reside but I am sure a "proper" Google search will yield the result for which you are looking.

```
hardy heron ppc installer
```



~s

---

### Post by dlabutte on 2008-04-25
Thank you for your email and for not quoting.
Thanks 
Dave L.

> **slacka-vt said:**
> Well my friend, you've come to the right place at the right time.
That fan problem you have on Ubuntu 6.06 "Dapper Drake" is due to the fact that
the kernel that comes installed with that version has no "thermal control" (fan control)

I agree with you completely that "Dapper" is/was the only version of Ubuntu that would install "properly" as it was "properly" supported for the PPC architecture.

The good news is that Ubuntu 8.04 "Hardy Heron" has just been officially released today !

Though there is no "official" PPC support, there is a PPC installer for your machine.

However, I have some bad news for you. 

I would be losing the respect of my comrades here on the Ubuntu Forum if I did not flame you repeatedly for not conducting a proper "search" of the forums to find the answers you have requested. There are an almost infinite amount of references to your issue.

Apparently, I am also not "allowed" to tell you where the PPC Ubuntu Hardy Install ISO images reside but I am sure a "proper" Google search will yield the result for which you are looking.

```
hardy heron ppc installer
```



~s

---

### Post by stream303 on 2008-04-25
Fortunately, the fan problem has been fixed if Feisty+, and I can verify that it works on PPC Hardy.  The only thing is, it will still scream upon initial installation, but will calm down after the first reboot.

You can go from Dapper to Hardy fortunetely, since they are both LTS releases, so you won't have to do a clean install:

[https://help.ubuntu.com/community/HardyUpgrades#head-db224ea9add28760e373240f8239afb9b817f197](https://help.ubuntu.com/community/HardyUpgrades#head-db224ea9add28760e373240f8239afb9b817f197)

Of course the repos are pretty well loaded up by now, so maybe wait a day or so.

---

### Post by dlabutte on 2008-05-19
I have installed 8.04 LTS and all is well. Thanks 4 info.

---

### Post by stream303 on 2008-05-19
The good thing is that this installation issue for some G5 owners might be fixed by the next spin, ie 8.04.1 since it was acknowledged by the devs.  Hopefully they'll be able to include the fix, but if not, just stay calm until the first reboot. :)

---

