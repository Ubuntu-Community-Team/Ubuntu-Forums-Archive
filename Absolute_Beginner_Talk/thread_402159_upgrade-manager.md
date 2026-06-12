---
title: "upgrade-manager"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by bionicyeti on 2007-04-05
When I run upgrade-manager from command line this is an error I get >>>

Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in ?
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 38, in        ?
    import apt
  File "/usr/lib/python2.4/site-packages/apt/__init__.py", line 8, in ?
    from apt.cache import Cache
  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 24, in ?
    import apt.progress
  File "/usr/lib/python2.4/site-packages/apt/progress.py", line 28, in ?
    import select
ImportError: No module named select

<<<

Any ideas???

---

### Post by mikeyphi on 2007-04-05
> **bionicyeti said:**
> When I run upgrade-manager from command line

I expect you mean update manager?
Normally operated from the GUI under SYSTEM - ADMINISTRATION
but what exactly were you wanting to do?

---

### Post by bionicyeti on 2007-04-05
Yeah, I meant update.

I was trying to upgrade to feisty. I tried running update-manager -d and nothing happened. Then I tried running the update manager via the gui and it wouldn't open. So I opened up a terminal window and ran it as sudo and thats the error I got. :confused:

---

### Post by jvc26 on 2007-04-05
Just a very brief point - you are, according to your profile using breezy - there is no way to upgrade to feisty without going through each distro in turn - 5.10 -> 6.06 -> 6.10 -> 7.04. As mentioned here:
> 
You can only upgrade to Feisty from Ubuntu 6.10 ("Edgy Eft")

From [here]("https://help.ubuntu.com/community/FeistyUpgrades")
Therefore to upgrade you have to do each in turn:
See [here]("https://help.ubuntu.com/community/UpgradeNotes")
That is most probably why you're having issues?
Il

---

### Post by bionicyeti on 2007-04-05
Profile is wrong. :( I'm running edgy.

---

