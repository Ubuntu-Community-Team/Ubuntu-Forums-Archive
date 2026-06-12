---
title: "Bug report help"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Pat L.I. on 2008-04-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/188579](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/188579) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello All, 

I have narrowed my broken wireless connection down to a virtualbox ose install and found a bug report online for it here - [bug #188579]("https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/188579")
The status of the bug report states Fix Released. Inside the bug report I notice some users have posted Workarounds.
My question is: Does "Fix released" mean that virtualbox has been fixed in the repositories? And therefore I should just be able to do ```
sudo aptitude install virtualbox-ose virtualbox-ose-modules-generic
```

If the above is the case then I am still experiencing the bug, do I re-open the bug report?
or does "Fix released" mean that there is a patch somewhere that I need to retrieve.

I am using Hardy Beta fully updated, However im posting here because this question relates to the proper use of bug reports!
thank you for any help in advance!
Pat

EDIT:
whoops! upon closer inspection of the bug report I need to select the modules package first ie. 
```
apt-get install virtualbox-ose-modules-generic virtualbox-ose
```

The question still stands though , is this still considered a bug when installed using my first method listed above?

---

### Post by Rocket2DMn on 2008-04-09
It looks like a fix has been released for the package, but the updated version is not available in the Ubuntu or Debian repositories yet, so it won't function without the workaround until the repos are updated with the version that has the fix included.
The modules package is "Fix Released", but for Ubuntu apt it is only "Triaged" which probably means it has been queued somewhere.  It is still "New" for the Debian repos, which means nobody has done anything about it yet.

---

